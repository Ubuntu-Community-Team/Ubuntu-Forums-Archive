---
title: "Unable To Launch GIMP"
date: 2011-07-23
forum: General Help
---

### Post by -kg- on 2011-07-23
I am running Kubuntu 11.04 on a Toshiba laptop on which I have had Ubuntu since Hardy.  I have used GIMP successfully on every installation I've had up to this one.  Now, I am unable to launch GIMP.

When I tried it initially, I couldn't get it to launch so on a lark I rebooted.  Same results.  I've also uninstalled and reinstalled it via KPackagekit, with the same results...it won't launch.

When I click on GIMP, I get the initial mini-bouncing icon, then that disappears.  On the bottom task bar there is a button that looks like GIMP is trying to load.  Then that disappears with no launching of GIMP.  I've checked System Monitor, but that shows nothing about GIMP running.

I love GIMP, but it's kind of useless if I can't run it.  I suppose I could pop into one of my other installed distros, but that's a PITA...I'd rather run it in my main installation.

My laptop is a Toshiba A135-S4487, 2GB RAM, Intel T5500 Duo-Core processor, running 64-bit Kubuntu 11.04.  I have beaucoup partition space available to Kubuntu, so space is not a problem...I have over 40 GB in my home partition, and a little over 15 GB for my root.  KDE Partition Manager shows neither filled very much...root is less than a third full and home is less than a 1/4.

Any ideas of what I could check/do?

---

### Post by IWantFroyo on 2011-07-23
What does it say if you type "gimp" in your terminal (Konsole)?

---

### Post by -kg- on 2011-07-24
I get the following:

> Satellite-A135:~$ gimp

(gimp:2829): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags ( 8 ) on option of type 0
Segmentation fault

<Edit>  I had to put spaces in the parentheses...it generated a smilie. :P

---

### Post by -kg- on 2011-07-24
Well, I've solved my own problem, thanks to you suggesting launching GIMP from the terminal and looking for error messages, IWantFroyo.  Thanks!

The answer is [in this thread]("http://kubuntuforums.net/forums/index.php?topic=3116721.msg262098#msg262098"), for those with the same problem who run across this thread.  The key information:

> There is a solution I found here about setting your gtk appearance to Raleigh, launch Gimp once, and then change back to whatever theme you were using before.

I did this and it worked perfectly.  I've changed gtk appearance back to oxygen and it still works.

I'll now mark this as solved.

---

