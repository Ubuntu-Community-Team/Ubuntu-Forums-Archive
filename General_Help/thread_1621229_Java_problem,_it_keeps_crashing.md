---
title: "Java problem, it keeps crashing"
date: 2010-11-14
forum: General Help
---

### Post by valvegrid on 2010-11-14
I'm having problems opening this site:

[http://www.highways.gov.uk/traffic/traffic.aspx](http://www.highways.gov.uk/traffic/traffic.aspx)

When I try and move the map or zoom in it keeps crashing Java. It doesn't seem to be browser specific as I've tried Firefox, Opera and Chrome and they are all doing the same, so it seems a Java problem.

If someone else can try it please and see if you get the same, just to make sure it's not my install. It used to work, it just seems in recent months it's given up the ghost. 

This is the only site I seemed to get a problem with, all the others that use Java heavily seemed to work.

I'm using 10.04 (Lucid) 1GB memory and AMD Sempron Processor 3400+

---

### Post by lykeion on 2010-11-14
Site works for me; takes a little while to initially load the map, but then zoom and scroll works ok.

What java browser plugin do you use - icedtea or sun java?
You can check this in firefox by entering *about:plugins* in the browser address field and look at the java entry.

---

### Post by valvegrid on 2010-11-14
Thanks for replying.

I notice that all three browsers are using Icedtea, I'll try and change that to Sun Java, I've just got to puzzle out how :)

---

### Post by lykeion on 2010-11-14
[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

plus that you might want to uninstall the *icedtea6-plugin* package

---

### Post by valvegrid on 2010-11-14
Thanks lykeion,

It's taken me all afternoon, but I got there in the end. I had to put a symbolic link it to make it work, but it all works perfectly now in all browsers.

---

### Post by dino99 on 2010-11-14
so change this thread to "SOLVED" please

---

### Post by valvegrid on 2010-11-14
> **dino99 said:**
> so change this thread to "SOLVED" please

You're a bit quick on my case, I'm trying to find it, just give me a chance, OK?

---

