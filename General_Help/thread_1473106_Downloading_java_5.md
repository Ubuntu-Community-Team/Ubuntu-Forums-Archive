---
title: "Downloading java 5"
date: 2010-05-04
forum: General Help
---

### Post by Blue_Jay on 2010-05-04
Hi,

I know this should be straight forward but I'm fairly new at this.. I'm trying to install java 5 on ubuntu 9.04 (Jaunty). I see it on the package list (though I am not entirely sure which provider it is).

I tried get-apt install sun-java5-jdk and I get the message that there is no package.

I added the multiverse distributor in the sources.list (extract below) even though the documentation indicates that universe and multiverse are enabled by default. 

Any idea what I'm doing wrong?

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiv$

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted multi$

---

### Post by Blue_Jay on 2010-05-04
Solved it.... needed to run apt-get update

---

