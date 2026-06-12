---
title: "Need help fast! unbut erros!"
date: 2012-04-27
forum: General Help
---

### Post by Gulliga on 2012-04-27
Pleas help me!
the following packages have unmet dependencies:  g++ : Depends: g++-4.4 (>= 4.4.5-1~) but it is not going to be installed        Depends: gcc-4.4 (>= 4.4.5-1~) but it is not going to be installed  gcc : Depends: gcc-4.4 (>= 4.4.5-1~) but it is not going to be installed        Recommends: libc6-dev but it is not going to be installed or                    libc-dev  libboost-regex1.42-dev : Depends: libicu-dev but it is not going to be installed  libboost1.42-dev : De

---

### Post by raja.genupula on 2012-04-27
```

sudo apt-get install -f 
```

try this

---

### Post by Gulliga on 2012-04-27
> **techsupport said:**
> Did you try using a guide to do a fresh install like this yet? That's fast.

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

What software are you trying to install in Ubuntu?

I dont have like that. i use putty to connect to the server...its a dedicated server

i need help!

---

### Post by techsupport on 2012-04-27
> **Gulliga said:**
> I dont have like that. i use putty to connect to the server...its a dedicated server

i need help!

Oh I thought you were doing a fresh install. My bad. More details about what you are doing would be helpful.

Can you be more specific?

Hang in there for someone to read your post.

---

### Post by Gulliga on 2012-04-27
> **techsupport said:**
> Oh I thought you were doing a fresh install. My bad. More details about what you are doing would be helpful.

Can you be more specific?

Hang in there for someone to read your post.

THIS
 apt-get install libboost1.41-dev libboost-system1.41-dev libboost-filesystem1.41-dev libboost-date-time1.41-dev libboost-regex1.41-dev libboost-thread1.41-dev libgmp3-dev liblua5.1-0 liblua5.1-0-dev liblua50 liblua50-dev liblualib50 liblualib50-dev lua50 lua5.1 libsqlite0-dev libsqlite3-dev sqlite3 libmysql++-dev libmysqlclient-dev mysql-client-5.1 mysql-server-5.1 mysql-common libxml2-dev libxml++2.6-dev cpp gcc g++ make automake autoconf pkg-config subversion liblua5.1-sql-mysql-dev liblua5.1-sql-sqlite3-dev zlib1g-dev zlib1g libcrypto++-dev libcrypto++8

---

### Post by techsupport on 2012-04-27
> **Gulliga said:**
> THIS
 apt-get install libboost1.41-dev libboost-system1.41-dev libboost-filesystem1.41-dev libboost-date-time1.41-dev libboost-regex1.41-dev libboost-thread1.41-dev libgmp3-dev liblua5.1-0 liblua5.1-0-dev liblua50 liblua50-dev liblualib50 liblualib50-dev lua50 lua5.1 libsqlite0-dev libsqlite3-dev sqlite3 libmysql++-dev libmysqlclient-dev mysql-client-5.1 mysql-server-5.1 mysql-common libxml2-dev libxml++2.6-dev cpp gcc g++ make automake autoconf pkg-config subversion liblua5.1-sql-mysql-dev liblua5.1-sql-sqlite3-dev zlib1g-dev zlib1g libcrypto++-dev libcrypto++8

You got some backstory on this so we can help you? What are you trying to do on what kind of system etc etc etc..   Can't help you with just that. I understand you want "fast" but we need to know what you are trying to do and the entire situation first.

So far we only know that you are using Putty to install something via secured shell on a remote system. What kind of system? Be specific. What software are you trying to install? Is this just an update? what?

---

### Post by Gulliga on 2012-04-27
> **techsupport said:**
> You got some backstory on this so we can help you? What are you trying to do on what kind of system etc etc etc..   Can't help you with just that. I understand you want "fast" but we need to know what you are trying to do and the entire situation first.

So far we only know that you are using Putty to install something via secured shell on a remote system. What kind of system? Be specific. What software are you trying to install? Is this just an update? what?


I am trying to get my website up. i am owner of a tibia server.

and i need Mysql to my server!

---

### Post by techsupport on 2012-04-27
> **Gulliga said:**
> I am trying to get my website up. i am owner of a tibia server.

and i need Mysql to my server!

You can try these guys:

[http://www.ubuntu.com/business/services/overview](http://www.ubuntu.com/business/services/overview)

Never heard of a tibia server. Maybe someone else here has configured one before. :)

---

