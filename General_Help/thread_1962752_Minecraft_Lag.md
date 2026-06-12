---
title: "Minecraft Lag"
date: 2012-04-21
forum: General Help
---

### Post by newtolinux101 on 2012-04-21
So when i first start minecraft it all works great no lag no nothing! My dell d620 laptop ran minecraft great on both and windows 7 and xp. but i have 11.10 now and about 1 min after starting the game it slows to a crawl i mean were talking like it paints the screen but only in game. i dont now whats causing this when my pc is good enough to play minecraft. 

system specs: 3 gb ram
100 gb ssd hard drive 
nvidia dual core graphics card (Maybe quad-core)
Intel dual-core processor 
dual booting windows 8 CP via wubi

and btw guys. i have no clue about tech or anything.

---

### Post by jerome1232 on 2012-04-21
Are you using OpenJDK or Oracles Java?

```
java -version
```

If you are using OpenJDK, you should get much better performance if you use Oracles Java.

[http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

---

### Post by newtolinux101 on 2012-04-21
JDK. it came from ubuntu software center

---

### Post by jerome1232 on 2012-04-21
> **newtolinux101 said:**
> JDK. it came from ubuntu software center

Yup, remove OpenJDK, grab the self extracting linux binary from the link I provided and install that, it *should* help.

---

### Post by newtolinux101 on 2012-04-21
can you walk me through how? i follow the instructions and it wont work. it says what do you want to open this program with

---

### Post by jerome1232 on 2012-04-21
Make sure the binary you downloaded is marked as executable, right click it, click permissions tab, check "Allow executing as a program" then double click it, select run in terminal.

---

