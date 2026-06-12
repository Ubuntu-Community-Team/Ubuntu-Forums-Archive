---
title: "Problem with installing Java"
date: 2011-10-08
forum: General Help
---

### Post by jcrad47 on 2011-10-08
Hi, I'm a new user of Ubuntu, and I'm trying to go about the steps for things that require java to work, but problem is the terminal keeps giving me problems. Such as:

I used this site: [http://compixels.com/6805/how-to-install-java-in-ubuntu-11-04-natty-narwhal-via-ppa](http://compixels.com/6805/how-to-install-java-in-ubuntu-11-04-natty-narwhal-via-ppa)

```
sudo add-apt-repository ppa:ferramroberto/java sudo apt-get update sudo apt-get install sun-java6-jre sun-java6-plugin
```The first step works but step 2 
"sudo apt-get update" gives me problems.

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

---

### Post by fooman on 2011-10-08
hello,  do like the error message tells you....try opening a terminal and type or copy/paste the following command into it:

```
 sudo dpkg --configure -a
```after that completes,  try:

```
sudo apt-get update
```hope that helps

---

