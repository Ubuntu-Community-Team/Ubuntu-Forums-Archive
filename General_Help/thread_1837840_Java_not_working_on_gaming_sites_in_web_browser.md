---
title: "Java not working on gaming sites in web browser"
date: 2011-09-02
forum: General Help
---

### Post by Reckinball on 2011-09-02
I have an older 2.0 ghz...compaq evo n610. I have tried running ubuntu as well as other distros using ubuntu. Everyone that I try I cannot get the java to load games on websites that use java. It loads the java logo and proceeds just like it would normally, but when the screen turns black and you get the loading screen. It just stays black after loading. Main site my son uses is

[http://www.nesplay.com/play/R.B.I._Baseball.html](http://www.nesplay.com/play/R.B.I._Baseball.html)

I have tried linux mint, ubuntu, zorin, ultimate, with same results.  While Elive, dream linux, and a few others it works on that comes preloaded with java.

Could someone try out this and let me know what it will take to get my sons laptop so he can play his games.

Thanks

---

### Post by dca on 2011-09-02
Your install is probably using openjdk and icedtea versus sun-java6 which is the proprietary version.  I believe by adding Ubuntu Restricted repo you can remove open and add proprietary version...

This might help after adding repo

[http://ejvyas.blogspot.com/2010/11/remove-open-jdk-and-installed-sun-java.html](http://ejvyas.blogspot.com/2010/11/remove-open-jdk-and-installed-sun-java.html)

---

