---
title: "Problems with java...again"
date: 2012-05-22
forum: General Help
---

### Post by blur xc on 2012-05-22
I'm trying to fix Java on my 11yr old son's laptop.  He's got a moc pages account (lego, my own creations) and they have a new java photo uploader that quit working for him.  I did all the install steps form the ubuntu website to get me on Java7, but the uploader isn't working.  All  I get is a message box stating "To use the new uploader, you'll need to install (or update) Java".  When I type in "java -version" in the terminal I get this-

```
jake@jake-laptop:~$ java -version
java version "1.7.0_04"
Java(TM) SE Runtime Environment (build 1.7.0_04-b20)
Java HotSpot(TM) 64-Bit Server VM (build 23.0-b21, mixed mode)

```

I'm at a loss, and I need to do the same for our main desktop computer too, once this is figured.  The Costco photo uploader also quit working on us...  Oh, and this computer is still running lucid.  How are things in 12.04?  Will upgrading (clean installs this time around) to 12.04 fix it on its own?

Thanks in advance-
BM

---

### Post by blur xc on 2012-05-22
No one?  Is Java working fine for everyone else??

---

### Post by scouser73 on 2012-05-22
> **blur xc said:**
> No one?  Is Java working fine for everyone else??

Hi, please follow the instructions set out here [[COLOR="Red"]**Easy Linux Tips Project Installing Java**[/COLOR]]("https://sites.google.com/site/easylinuxtipsproject/java")

The instructions are set out clearly and you will have no problem getting Java to work correctly.

***I have used this method myself and can confirm it works perfectly.***

---

### Post by QIII on 2012-05-22
You have the JRE installed, but apparently not the plugin.

For an easier method than above, see the link in my signature.

---

### Post by blur xc on 2012-05-25
Thanks!  I don't remember how I got there, but I originally installed it step by step via some instructions on the Ubuntu website (I think!!), but the Webup8 ppa did the trick.  Those guys do some good work over there...  

Thanks again-
BM

---

