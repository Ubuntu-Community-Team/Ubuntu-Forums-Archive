---
title: "Websphere silent install fails on ubuntu 10.10"
date: 2011-04-15
forum: General Help
---

### Post by Surendra on 2011-04-15
I am trying to install in Silent mode on Ubuntu 10.10 desktop. When i ran the cmd, doesn't get any messages.

[B]root@home:/var/tmp/WebSphere/WAS# ./install -options responsefile.nd.txt -silent
root@home:/var/tmp/WebSphere/WAS#
[/B]

I tried this :
root@home:/var/tmp/WebSphere/WAS# [B]./install -options responsefile.nd.txt -silent -is:javaconsole
/var/tmp/WebSphere/WAS/../JDK/jre.pak/repository/package.java.jre/java/jre/bin/java: 1: Syntax error: "(" unexpected[/B]
root@home:/var/tmp/WebSphere/WAS# 


Can anybody suggest how to fix this.

---

### Post by chughgaurav on 2011-10-22
You may find the installation steps in this video -[http://www.youtube.com/watch?v=_XW6qCkG5ko.]("http://www.youtube.com/watch?v=_XW6qCkG5ko")

---

