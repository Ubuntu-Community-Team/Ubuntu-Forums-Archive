---
title: "new user questions"
date: 2009-06-30
forum: General Help
---

### Post by henry2264 on 2009-06-30
iv'e order the new ubuntu cd to be sent out and before i even begin i want to ask if anybody knows if windows vista programs will work on it ie, anything from slysoft, utorrent, orbit downloader, nero, easttec eraser, winzip 11 pro, eset nod32 v4, klite codec pack
 
the reason i ask is that i've been using these programs awhile now and find them invaluable for my needs and theres also quite a few out there that i know are meant for windows and just would like to know if ubuntu is backwards compatable for windows stuff on my HP DV6207TX
 
thanks

---

### Post by t4thfavor on 2009-06-30
There are equivaents for all of the mentioned  apps, most are better than their windows bretheren.
utorrent will work for sure thugh, and winzip? haven't you heard or rar yet?


You can get a good share of windows progams to run on ubuntu, but truth is you wont really need to.

Oh, and welcome to the club :)

---

### Post by credobyte on 2009-06-30
Let's start with a simple rule - Linux is not Windows and you can't run Windows applications without using additional software like Wine ( or VirtualBox ).
I know that you can run uTorrent under Wine, but .. for other apps, let's wait for someone else to answer this question !

If you really need some applications and they can't be used under Ubuntu, install XP or Vista ( depends on RAM ) on VirtualBox :)

---

### Post by QIII on 2009-06-30
Are you planning to ditch Windows altogether, or dual boot (or ...?)?

If you are going to get rid of Windows, Wine has been mentioned as a sandbox in which to run Windows programs.

You will have to dig around a bit, but there is a database of programs that run in Wine and their ratings here:

[http://appdb.winehq.org/index.php](http://appdb.winehq.org/index.php)

---

### Post by henry2264 on 2009-06-30
im looking to run linux on it's own because im tired of vista constantly crashing and freezing
 
i like winzip just because of its simple to use interface and never had a need to try rar yet
 
like the look of wine and i think that program alone will sort out all my windows prog needs
 
thanks

---

### Post by t4thfavor on 2009-07-01
> **henry2264 said:**
> im looking to run linux on it's own because im tired of vista constantly crashing and freezing
 
i like winzip just because of its simple to use interface and never had a need to try rar yet
 
like the look of wine and i think that program alone will sort out all my windows prog needs
 
thanks
I wouldn't say all, but a good bit. You will see that most of that stuff is either unnecessary, or built in. As in the virus scanner, not needed here. and WinZip, also not needed as the functioality is built into the OS.

---

### Post by 3rdalbum on 2009-07-01
> **henry2264 said:**
> i like winzip just because of its simple to use interface and never had a need to try rar yet

Ubuntu comes with a simple-to-use archive manager called File Roller. You'll probably like it. It can handle more than Zip, too.
 
> like the look of wine and i think that program alone will sort out all my windows prog needs

As someone who's used Wine: No, it won't.

Wine is a fallback, last-ditch effort to run Windows programs. It doesn't work with very many Windows programs at all - it's an incredibly difficult task to reverse-engineer Windows.

The best way two ways to explain it are this:

1. [http://upload.wikimedia.org/wikipedia/commons/7/7c/History_Of_WineAppDB.gif](http://upload.wikimedia.org/wikipedia/commons/7/7c/History_Of_WineAppDB.gif)

It's an animated graph showing Wine's application compatibility through the last few years. There are as many programs reported as running "Perfectly" through Wine as there are reported as "not running at all". For the levels in between, you may need to do some hackery to get the programs working.

**BUT** usually, if you find that a program runs in Wine, you rush off and report it to the developers - if you find that a program doesn't run in Wine, you usually just give up. This *skews the statistics* and makes Wine look better than it is.

2.

"Trying to run all your Windows programs in Wine == sad Linux user.
Finding native Linux equivalents wherever possible == happy Linux user."

Everything you've listed is either unnecessary on Ubuntu, or has an excellent Linux-native equivalent available from the repositories.

---

