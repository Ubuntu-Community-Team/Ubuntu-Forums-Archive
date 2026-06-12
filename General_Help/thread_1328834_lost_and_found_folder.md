---
title: "lost and found folder"
date: 2009-11-16
forum: General Help
---

### Post by mjwilson1313 on 2009-11-16
I dont even know what this folder is, but when i try to open it it says i dont have permission. Im new to ubuntu and am running hardy, and so far reaaly enjoy it.(with the exeception of the msttcorefonts error status 1 that always comes up) haha. But if you could explain what that folder is or how to open it I would be very apprceative.

---

### Post by mechro on 2009-11-16
Lost & Found is a general Linux system folder...

> /lost+found - Linux should always go through a proper shutdown. Sometimes
your system might crash or a power failure might take the machine down.
Either way, at the next boot, a lengthy filesystem check using fsck will
be done. Fsck will go through the system and try to recover any corrupt
files that it finds. The result of this recovery operation will be placed
in this directory. The files recovered are not likely to be complete or
make much sense but there always is a chance that something worthwhile is
recovered.

You can access it as root (sudo) but there's little point. Don't worry about it.

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
[https://answers.launchpad.net/ubuntu/+question/8373](https://answers.launchpad.net/ubuntu/+question/8373)

---

### Post by Bradj47 on 2009-11-16
No idea. I've seen directory on other Unix-like OS including Solaris and I've never figured out what it was. I just searched the Ubuntu forums and came up with this: [http://ubuntuforums.org/showthread.php?t=388610](http://ubuntuforums.org/showthread.php?t=388610)

---

### Post by audiomick on 2009-11-16
The folder belongs to "root", i.e. the system administrator. It's function has to do with keeping the file system in order. Leave it alone. It has a reason for being and is there to help you. :-)

---

### Post by mjwilson1313 on 2009-11-16
ok thanks everyone for the quick reply.... i guess by concensus i will leave it alone

---

### Post by mjwilson1313 on 2009-11-16
oh and SOLVED

---

### Post by t0p on 2009-11-16
> **mjwilson1313 said:**
> when i try to open it it says i dont have permission..

Generally, when you try to do something and are told that you "don't have permission", this means you need to have administrative privileges to do that thing.

How to gain admin privileges depends on what you are trying to do:

[LIST]
[*]If you're trying to run a command in a terminal, prefix the command with **sudo**;
[*]If you're trying to run a program with graphical interface, hit **Alt+F2** and type in **gksudo <name of command>**.
[/LIST]
You'll find a full explanation of **sudo** and **gksudo** [here]("https://help.ubuntu.com/community/RootSudo").  I strongly advise you to click on that link and read the article.  Use of **sudo**/**gksudo** is *very* important in Ubuntu.  It's something that you really need to understand.

---

