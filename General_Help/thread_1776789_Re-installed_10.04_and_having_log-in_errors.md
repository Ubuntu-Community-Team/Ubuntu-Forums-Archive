---
title: "Re-installed 10.04 and having log-in errors"
date: 2011-06-06
forum: General Help
---

### Post by littlebird on 2011-06-06
I recently re-installed Lucid onto my desktop PC, and I am having no end of trouble with it!  When I turn the computer on and log in, I am automatically logged in to a user defined session.  I have tried changing the session definition before logging in (safe mode), and have had no luck.  I have tried re-installing again, and the problem remains.  Any ideas?

Note:  I have successfully used the same disc to install this system before, but had data loss.  The data was recovered, and now the problems are showing up.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **littlebird said:**
> I recently re-installed Lucid onto my desktop PC, and I am having no end of trouble with it!  When I turn the computer on and log in, I am automatically logged in to a user defined session.  I have tried changing the session definition before logging in (safe mode), and have had no luck.  I have tried re-installing again, and the problem remains.  Any ideas?

Note:  I have successfully used the same disc to install this system before, but had data loss.  The data was recovered, and now the problems are showing up.

Do a check of your Disk Status in Disk Utilities?   What does it tell you when you check with Disk Utility? Look in Disk STATUS  :)

---

### Post by littlebird on 2011-06-06
Unfortunately I have no desktop icons or dropdown menus, so I can't access any of my utilities without creating a launcher.  I don't have enough experience with this area of Ubuntu to know how to get there.  All I have is a blank screen with my background photo.

---

### Post by linuxinstalledfromhdd on 2011-06-06
Does this happen with a live disc of Ubuntu?

---

### Post by littlebird on 2011-06-07
No, I installed the system with a system image disc.  However, when I tried the "use before installing" feature of the system image disc and ran it live instead, I was able to use the desktop environment normally.   I am wondering if the IT guy who did the data recovery for me inadvertently did something to the file systems?  Apparently Linux is not their area of expertise.  Is there any information you need to help solve the problem?

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **littlebird said:**
> No, I installed the system with a system image disc.  However, when I tried the "use before installing" feature of the system image disc and ran it live instead, I was able to use the desktop environment normally.   I am wondering if the IT guy who did the data recovery for me inadvertently did something to the file systems?  Apparently Linux is not their area of expertise.  Is there any information you need to help solve the problem?

Here is what I would do if I was unsure.  Contact them and ask for as many specifics about what they did.  They they can't do that I would go off the assumption that they probably don't know what they are doing with Linux.  I would ask for a partial refund at some point if you can fix this yourself too.

Start fresh.. :) And that way you know exactly what is going on.. 

Download a ISO of Ubuntu.  Preferablly 10.10, since that seems to work for most people right now.    Install that to a USB Flash Drive. You can find out how to create a live flash drive of Ubuntu by selecting number two from this page [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)   It just makes the installation process that much smoother and faster too.  Boot from the USB Flash Drive, and select Install.  You are going to get to a screen that allows to install it side-by-side your existing systems..  It will then resize the partision to make some space..   And install everything else for the base system..  After you get that running, and you're booting from the hard drive again and your newly installed Ubuntu 10.10.. use this guide to get everything perfect, and then you can migrate your data over from the other partitions. If you get stuck at that point, let us know so we can walk you through the data migration process.

Here is the guide, and links to the 10.10 iso file:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by littlebird on 2011-06-07
thank you, I will give that a try.  I spoke to a computer repair friend today who thinks the hard drive might have sustained some damage from the data recovery process because it is a bit old, but perhaps it will still work (hopefully!).

---

### Post by linuxinstalledfromhdd on 2011-06-07
I suggest purchasing a new hard drive ASAP. 

And do a fresh installation on that instead. :) 

:popcorn:

---

### Post by dFlyer on 2011-06-07
Boot off the live cd and check your hard drive using disk utility. Sounds like it could be failing. I would backup as much data as you can that you want to keep.

---

### Post by littlebird on 2011-06-14
That was the consensus I came to with my IT friend.  I have an old laptop that is a bit faster than this other computer, so I think I'll just move the recovered data to it and part out the old one.  Thanks for all the input!  I appreciate it.

---

