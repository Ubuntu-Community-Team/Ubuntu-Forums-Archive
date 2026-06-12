---
title: "javac not found"
date: 2009-09-08
forum: General Help
---

### Post by aneuryzma on 2009-09-08
hi,

if I type javac file.java it works

If I run a "make" file (I assume invoking javac) I get the following message:

javac not found

Why doesn't it work inside the make command ?

thanks

---

### Post by nikhilk on 2009-09-08
> **aneuryzma said:**
> hi,

isn't java already installed in Ubuntu ?

I get the following message when I want to compile a file:

javac not found

You need to install either sun-java5-jdk or sun-java6-jdk pacakge for that.

---

### Post by aneuryzma on 2009-09-08
Hi sorry,

I've edited my message because I noticed javac is working outside the make command.

Actually it is a bit strange. If I try to run javac this is what I get

> $ javac Agent.java

The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.3
 * java-gcj-compat-dev
 * gcj-4.2
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: javac: command not found

---

### Post by nikhilk on 2009-09-08
> **aneuryzma said:**
> I've edited my message because I noticed javac is working outside the make command.

I do not understand your comment. At the end of the output you have posted, I see the error
> bash: javac: command not found 

Are you sure you have javac? What is the output of the following command?
```
which javac
```

---

### Post by aneuryzma on 2009-09-08
I also don't understand it indeed.

At the end of the output it says "not found" and at the begin it says "can be found".

which javac doesn't give any output. It go to next line.

How can I fix it ?



thanks

---

### Post by nikhilk on 2009-09-08
> **aneuryzma said:**
> I also don't understand it indeed.

At the end of the output it says "not found" and at the begin it says "can be found".

which javac doesn't give any output. It go to next line.

How can I fix it ?



thanks

Both sun-java5-jdk or sun-java6-jdk packages provide javac.

You need to install either one of those, depending on your requirement.
```
sudo aptitude install sun-java5-jdk
```
or
```
sudo aptitude install sun-java6-jdk
```

---

### Post by aneuryzma on 2009-09-08
ok thanks, now it works

---

