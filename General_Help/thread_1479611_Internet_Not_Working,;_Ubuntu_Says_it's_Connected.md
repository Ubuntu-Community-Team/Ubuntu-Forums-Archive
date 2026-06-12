---
title: "Internet Not Working,; Ubuntu Says it's Connected"
date: 2010-05-10
forum: General Help
---

### Post by flowingfire on 2010-05-10
Hi there!  My wireless Internet manager in the upper right-hand corner of my Ubuntu desktop consistantly says it's connected to my wireless network between 75%-85% connection strength.

I can go into the terminal, and ping any website.  It will ping it and show repeated entries.  So, I assume the Internet is working.

Yet, I can open Mozilla Firefox and it won't work.  Neither will software updates.  No software that connects to the Internet can connect.  It will display in Firefox, "The server at "www._____.com is taking too long to respond."  No matter what website, no matter how many times I restart the computer, and no matter how many times I reset the router, nothing works.

So... Ubuntu says I have Internet available.... Why can't it work?  I got some advice from the people on chat to adjust some network settings to fix it, but it didn't work.... ??????????

The Internet works just fine on other computers on this network, and on the same one when logged into Windows instead of Linux.

?????????????????????

I am running Ubuntu 10.0.4

---

### Post by bobcollard on 2010-05-11
> **flowingfire said:**
> Hi there!  My wireless Internet manager in the upper right-hand corner of my Ubuntu desktop consistantly says it's connected to my wireless network between 75%-85% connection strength.

I can go into the terminal, and ping any website.  It will ping it and show repeated entries.  So, I assume the Internet is working.

Yet, I can open Mozilla Firefox and it won't work.  Neither will software updates.  No software that connects to the Internet can connect.  It will display in Firefox, "The server at "www._____.com is taking too long to respond."  No matter what website, no matter how many times I restart the computer, and no matter how many times I reset the router, nothing works.

So... Ubuntu says I have Internet available.... Why can't it work?  I got some advice from the people on chat to adjust some network settings to fix it, but it didn't work.... ??????????

The Internet works just fine on other computers on this network, and on the same one when logged into Windows instead of Linux.

?????????????????????

I am running Ubuntu 10.0.4
Read this post, near the middle is the main reason, chaosgrimm found settings were changed and need to be changed back.
[http://ubuntuforums.org/showthread.php?t=1451064](http://ubuntuforums.org/showthread.php?t=1451064)

---

### Post by flowingfire on 2010-05-16
Hey there.  I checked on the link, and made the modifications.  It didn't actually help.

I asked a friend who is very good with Debian-based distributions to take a look, and he could get the Internet to work when launching browsers by command-line only.... ?????? strange....  It still doesn't fix the problem, unfortunately, since I'm not that good with command line unless somebody tells me what to do.

That said, I'm not sure what to do here anymore.

---

### Post by davethawley on 2010-09-16
Just had the same with ubuntu 10.0.4. Thanks for the  tip flowingfire. It seems to be perhaps a security issue. I can only run firefox from the commandline when I am a root (or whatever they are called nowadays) I need to type sudo firefox <Ret> this works fine. If I don't run as a superuser then it doesn't work

Cheers
Dave

---

