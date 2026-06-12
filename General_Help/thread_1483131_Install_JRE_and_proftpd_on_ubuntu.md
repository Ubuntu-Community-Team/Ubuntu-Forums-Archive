---
title: "Install JRE and proftpd on ubuntu"
date: 2010-05-14
forum: General Help
---

### Post by dp92 on 2010-05-14
last time i used ubuntu i just typed
apt-get install sun-java6-jre
apt-get install proftpd

now i get an error messege
```
root@hostname:~# apt-get install proftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package proftpd

```

what is the problem?

(i am using ubuntu 9.04 server)

---

### Post by CoreyB. on 2010-05-14
In Lucid and Karmic, [proftpd]("http://packages.ubuntu.com/karmic/proftpd") is a virtual package, so it doesn't really exist.  Use proftpd-basic instead.

---

### Post by dp92 on 2010-05-14
same:
```
E: Couldn't find package proftpd-basic

```

---

### Post by dino99 on 2010-05-14
and gadmin-proftpd for config with gtk+

---

### Post by dino99 on 2010-05-14
> **dp92 said:**
> same:
```
E: Couldn't find package proftpd-basic

```

can't you have access to repo ? are they activated ?

---

### Post by gmargo on 2010-05-14
You need to enable the "universe" repository to get proftpd-basic.
[http://packages.ubuntu.com/lucid/proftpd-basic](http://packages.ubuntu.com/lucid/proftpd-basic)

For the JRE, you probably have to install the openjdk-6-jre package.
[http://packages.ubuntu.com/lucid/openjdk-6-jre](http://packages.ubuntu.com/lucid/openjdk-6-jre)

---

