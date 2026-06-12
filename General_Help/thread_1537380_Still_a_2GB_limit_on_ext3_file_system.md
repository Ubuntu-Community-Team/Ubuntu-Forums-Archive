---
title: "Still a 2GB limit on /ext3 file system"
date: 2010-07-23
forum: General Help
---

### Post by swilson8224 on 2010-07-23
Folks:
Thank you for the potential help.  I am a fairly newbie to Linux.  With version 8.04 I have a drive formatted in ext3 that still is experiencing a 2gb limit. 
 
Background:  I have a SCO 5.0.7 box with files I need to tar to my ubuntu box.  I set up a NFS on ubuntu and mapped from SCO no problem.  When I tar from SCO to Ubuntu I hit a 2gb limit.  Testing my Ubuntu environment I try to cat big1.tgz big2.tgz > big3.tgz and big3.tgz is stopped at 2gb too......so I cannot create a file bigger than 2gb on my ext3 filesystem.......waz up with that?
 
Scott in Fort Mill, SC

---

### Post by j7%&lt;RmUg on 2010-07-23
Too much to explain here:

[http://linuxmafia.com/faq/VALinux-kb/2gb-filesize-limit.html](http://linuxmafia.com/faq/VALinux-kb/2gb-filesize-limit.html)

Have a read of that, it will tell you what you need to know.

Can i ask, why are you still using 8.04?

10.04 has been out since april and its an LTS just like 8.04.

---

### Post by swilson8224 on 2010-07-24
Thank you, that helped greatly.  My box is 8.04 because it arrived to me as a broken LeftHand NSM200.  For 300.00 I got 2 4x4 drive arrays.  Totally diskless install over a PXE boot.  I tried 9 but the mini.iso didn't see my nic cards and 10 didn't have a PXE boot option compiled yet.
The size of my files changes so slowly I think I can just program 2 separate gets to stay below 2gb's...or dedicate a new box to it.  I was very impressed how smoothly 10 went on a old Dell Dim.

---

### Post by prodigy_ on 2010-07-24
> The new maximum size of an individual file is 8 terabytes (2^63)
Actually 2^63 bytes is 8 [exbibytes](http://en.wikipedia.org/wiki/Exbibyte).

---

### Post by Zill on 2010-07-24
> **nisshh said:**
> ...Can i ask, why are you still using 8.04?...
Some of us *do* still use earlier versions for various reasons. ;-)  As desktop 8.04 is still officially supported until April 2011 and server until April 2013 there is nothing wrong with that.

There are many advantages in updating to later versions but, sometimes, "if it ain't broke don't fix it"!

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

---

