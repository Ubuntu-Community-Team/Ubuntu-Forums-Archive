---
title: "IDE not working in lucid lynx"
date: 2010-04-29
forum: General Help
---

### Post by JPA2 on 2010-04-29
I've just upgraded from 9.10 and everything is good, accept that netbeans will not load.
I get the netbeans 6.8  splash screen then nothing.  Anyone else having this type of problem?  Any suggestions would be appreciated!

---

### Post by jfcarr on 2010-04-30
No solution, I'm afraid.  I just wanted to note that I am having exactly the same problem.

---

### Post by jfcarr on 2010-04-30
The first time I tried to open Netbeans, I saw a warning dialog telling me that my plugins were incompatible with Netbeans 6.8, and asking if I wanted to disable them.  I answered in the affirmative, but now Netbeans won't load at all beyond the splash screen.

---

### Post by JPA2 on 2010-04-30
I have resolved this by using sudo apt-get remove --purge netbeans and then,
sudo apt-get install netbeans.  I hope this helps anyone who is having the same problems.:P

---

### Post by doas777 on 2010-04-30
if you haven't already fixed it, are you sure you have sun java installed?
what is the output of 
```

javac -version
java -version

```

---

### Post by dlumpp on 2010-04-30
Purging fixed it for me. I had the same issue. Thanks!

---

### Post by r-senior on 2010-04-30
If you NetBeans people are using Maven, this might save you a search ...

[https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/554134]("https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/554134")

My NetBeans launched but I had to work through importing the plugins one by one until I found which was causing a problem.

---

