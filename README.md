#!/bin/bash

## usage

    usage(){
        echo "usage:"
        echo
        echo "    $0 <package>"
        echo 
        echo "packages:"
        echo 
        sed -n 's/^###/   /p' $0
    }

## packages

### erlang

    erlang(){
        sudo sh -c 'echo "deb http://binaries.erlang-solutions.com/debian $(lsb_release -sc) contrib" > /etc/apt/sources.list.d/erlang.list'
        wget -O - http://binaries.erlang-solutions.com/debian/erlang_solutions.asc | sudo apt-key add -
        sudo apt-get update
        sudo apt-get install esl-erlang
    }

### java

    java(){
        sudo add-apt-repository ppa:webupd8team/java
        sudo apt-get update
        sudo apt-get install oracle-java7-installer
    }

### mongodb

    mongodb(){
        sudo sh -c 'echo "deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen" > /etc/apt/sources.list.d/mongo.list'
        sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
        sudo apt-get update
        sudo apt-get install mongodb-10gen
    }

### neo4j

    neo4j(){
        sudo sh -c 'echo "deb http://debian.neo4j.org/repo stable/" > /etc/apt/sources.list.d/neo4j.list'
        wget -O - http://debian.neo4j.org/neotechnology.gpg.key | sudo apt-key add - 
        sudo apt-get update
        sudo apt-get install neo4j
    }

### nginx

    nginx(){
        sudo apt-add-repository ppa:nginx/stable
        sudo apt-get update
        sudo apt-get install nginx
    }

### nodejs

    nodejs(){
        sudo apt-add-repository ppa:chris-lea/node.js
        sudo apt-get update
        sudo apt-get install nodejs
    }

### rabbitmq
    
    rabbitmq(){
        sudo sh -c 'echo "deb http://www.rabbitmq.com/debian/ testing main" > /etc/apt/sources.list.d/rabbitmq.list'
        wget -O - http://www.rabbitmq.com/rabbitmq-signing-key-public.asc | sudo apt-key add -
        sudo apt-get update
        sudo apt-get install rabbitmq-server
    }

### redis

    redis(){
        sudo apt-add-repository ppa:chris-lea/redis-server 
        sudo apt-get update
        sudo apt-get install redis-server
    }

### rethinkdb

    rethinkdb(){
        sudo add-apt-repository ppa:rethinkdb/ppa
        sudo apt-get update
        sudo apt-get install rethinkdb
    }

### riak

    riak(){
        # sudo sh -c 'echo "deb http://apt.basho.com $(lsb_release -sc) main" > /etc/apt/sources.list.d/basho.list'
        sudo sh -c 'echo "deb http://apt.basho.com precise main" > /etc/apt/sources.list.d/basho.list'
        wget -O - http://apt.basho.com/gpg/basho.apt.key | sudo apt-key add -
        sudo apt-get update
        sudo apt-get install riak
    }

### elasticsearch

    elasticsearch(){
        wget -O - http://packages.elasticsearch.org/GPG-KEY-elasticsearch | sudo apt-key add -
        sudo sh -c 'echo "deb http://packages.elasticsearch.org/elasticsearch/1.1/debian stable main" > /etc/apt/sources.list.d/elasticsearch.list'
        sudo apt-get update
        sudo apt-get install elasticsearch
    }

### tmux

    tmux(){
        sudo add-apt-repository ppa:pi-rho/dev
        sudo apt-get update
        sudo apt-get install tmux
    }

### rust

    rust(){
        sudo add-apt-repository ppa:hansjorg/rust
        sudo apt-get update
        sudo apt-get install rust-nightly
    }

### php

    php(){
        sudo add-apt-repository ppa:ondrej/php5
        sudo apt-get update
        sudo apt-get install php5
    }

## main

    if [[ $# = 0 ]]; then
        usage
    else
        $1
    fi

