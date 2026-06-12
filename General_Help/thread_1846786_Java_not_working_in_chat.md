---
title: "Java not working in chat"
date: 2011-09-19
forum: General Help
---

### Post by derekreilly on 2011-09-19
Hi,

I'm using Ubuntu 11.04 64 bit. For some reason when using java chat rooms, java has stopped loading. It worked for weeks then suddenly the page partly loads but there is just a grey box where the java window should load.

The same thing happened a month or so ago but it suddenly came back again a few days later. I've tried it on Firefox, Chromium and Opera...nothing. Also happens with Linux Mint 11.04

Any ideas?

---

### Post by lordbux on 2011-09-19
tell which one you have installed

iced tea java
or sun java

---

### Post by derekreilly on 2011-09-19
> **lordbux said:**
> tell which one you have installed

iced tea java
or sun java

sun java 6

---

### Post by Zephilinox on 2011-09-20
there is probably just something wrong with the website itself

You should follow this wiki page and install openjdk and icedtea [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) not sure if it will help though

once you've installed those, run ```
sudo update-alternatives --config java

``` to switch to using openjdk rather than sunjava.

---

### Post by derekreilly on 2011-09-20
Hi Zephilinox,

It's working, thanks!!

Derek.

---

