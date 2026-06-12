---
title: "Ubuntu 10.04 display freeze up"
date: 2010-05-07
forum: General Help
---

### Post by aaron94 on 2010-05-07
Hello,

I am having the most annoying problem with Ubuntu. It seems that the display will just randomly freeze up. Sometimes it will happen after a few minutes, other times longer, or not at all. 

This is very annoying as I have to manually reboot when it does this because I cannot move the mouse. 

If there is any fix for this it would be appreciated. Thanks.

---

### Post by Catharsis on 2010-05-07
Which version of Ubuntu do you have?

Also, what graphics card do you have?
```
lspci | grep VGA
```

---

### Post by aaron94 on 2010-05-07
Ubuntu 10.04 64-bit

aaron@aaron-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
aaron@aaron-desktop:~$

I have also installed my latest graphics card driver from System-Admin-Hardware Drivers, but I can confirm that I was having the problem before that.

---

### Post by aaron94 on 2010-05-07
Any help please?

---

### Post by StuartN on 2010-05-07
> **aaron94 said:**
> Any help please?

Possible Sleep/Hibernation issues with 10.04? [http://ubuntuforums.org/showthread.php?t=1469167](http://ubuntuforums.org/showthread.php?t=1469167)

[10.04] Ubuntu freeze because of Firefox? [http://ubuntuforums.org/showthread.php?t=1469650](http://ubuntuforums.org/showthread.php?t=1469650)

Lucid Freezes Randomly [http://ubuntuforums.org/showthread.php?t=1470452](http://ubuntuforums.org/showthread.php?t=1470452)

Hibernate & Suspend- can't wake up [http://ubuntuforums.org/showthread.php?t=1472860](http://ubuntuforums.org/showthread.php?t=1472860)

10.04 false I/O errors and random freezes [http://ubuntuforums.org/showthread.php?t=1473131](http://ubuntuforums.org/showthread.php?t=1473131)

Display Freezes - Fresh 10.04 install [http://ubuntuforums.org/showthread.php?t=1474730](http://ubuntuforums.org/showthread.php?t=1474730)

---

### Post by aaron94 on 2010-05-07
> **StuartN said:**
> Possible Sleep/Hibernation issues with 10.04? [http://ubuntuforums.org/showthread.php?t=1469167](http://ubuntuforums.org/showthread.php?t=1469167)

[10.04] Ubuntu freeze because of Firefox? [http://ubuntuforums.org/showthread.php?t=1469650](http://ubuntuforums.org/showthread.php?t=1469650)

Lucid Freezes Randomly [http://ubuntuforums.org/showthread.php?t=1470452](http://ubuntuforums.org/showthread.php?t=1470452)

Hibernate & Suspend- can't wake up [http://ubuntuforums.org/showthread.php?t=1472860](http://ubuntuforums.org/showthread.php?t=1472860)

10.04 false I/O errors and random freezes [http://ubuntuforums.org/showthread.php?t=1473131](http://ubuntuforums.org/showthread.php?t=1473131)

Display Freezes - Fresh 10.04 install [http://ubuntuforums.org/showthread.php?t=1474730](http://ubuntuforums.org/showthread.php?t=1474730)

Reading these topics, it seems that I am not the only one with these problems! 

In one topic, it mentions a buggy version of GLX (1.4) that causes leaks. That is the version I have. Any suggestions on fixing this?

---

### Post by Catharsis on 2010-05-08
I found this. Hopefully it'll help with the GLX problem.

[https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

---

### Post by sillyboy on 2012-07-28
> **Catharsis said:**
> I found this. Hopefully it'll help with the GLX problem.

[https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

When one clicks on the above link the page says "this page does not exist yet".  WTF???

---

### Post by GreatDanton on 2012-07-28
it's old thread ;)

---

### Post by wildmanne39 on 2012-07-28
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

