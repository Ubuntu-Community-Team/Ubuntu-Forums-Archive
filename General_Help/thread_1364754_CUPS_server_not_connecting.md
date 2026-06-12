---
title: "CUPS server not connecting"
date: 2009-12-26
forum: General Help
---

### Post by shendric on 2009-12-26
I've noticed that a lot of folks are having problems with the CUPS server lately.  Well, here's another one.  After a reboot this morning, my CUPS server doesn't connect.  When I try to connect, I get this error:

There was an error during the CUPS operation: 'httpConnectionEncrypt failed'.

When I try to restart CUPS, I get the following:

* Restarting Common Unix Printing System: cupsd                                cupsd: Child exited on signal 15!

I decided to look at my cupsd.conf, based on another thread, and my cupsd.conf seems to be empty.  Nothing there.

Any ideas what's happening, or how I can get cupsd.conf back again?  I've tried reinstalling cups, but no dice.

I'm on 64-bit Jaunty, if that helps.

---

### Post by shendric on 2009-12-26
I was able to get the printer working again by copying cupsd.conf.O into cupsd.conf.  However, I'm mystified as to why my cupsd.conf went away to begin with.  Any thoughts as to why?

Just curious, at this point.

---

### Post by jmlynn on 2009-12-26
I was successful in installing Ubunto into my Toshiba machine, using high resolution in the internal LCD and medium resolution on the external LCD screen.

But when I use System/Admiinistration/Hardware Drivers and installed the "recommended" NVIDIA accelerated graphics driver (version 185), it failed duing install with the following error:
"System error: installArchives() failed"

The drivers "was not installed", but when I reboot, and click the disply, now I got an error 

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

If I click yes, I will get the "advanced NVIDIA" screen that I have no clue of how to configure it.

If I click no, I got a low resolution desktop that I lost the ability to use two screens with the external LCD being the extended screen.

How do I restore it back to the "Ubuntu configured display drivers" without having to reinstall Ubunto (which I had done multiple times since I started this journey of getting reacquainted with Linux)

Appreciate any help.

Jeff

---

### Post by stardotstar on 2010-01-03
> **shendric said:**
> I was able to get the printer working again by copying cupsd.conf.O into cupsd.conf.  However, I'm mystified as to why my cupsd.conf went away to begin with.  Any thoughts as to why?

Just curious, at this point.

I ran into this today - not sure when it happened and I don't know the reason cups got broke.  I managed to fix it with a complete removal and reinstall of CUPS.  The printer was automatically detected and worked straight away.  I elected to do a fresh install as I suspected it was caused by an update or upgrade and hope that it will now be in sync with the rest of the updated system.  Can't confirm if your approach would have worked for me since I only just saw this - but the Remove Completely and then reinstall (no restarts needed etc) works too.

Will

---

### Post by bubblehead74 on 2010-01-05
I also had this problem, and it looks like the culprit was xpdf-tools package.

---

### Post by nike984 on 2010-03-05
as Lutz pointed out in the following link, 
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/335898/comments/7](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/335898/comments/7)
it could be an AppArmor issue. 

Try ```

sudo aa-complain cupsd
sudo /etc/init.d/cups restart
```

It worked for me. ;)

---

### Post by jmlynn on 2011-07-20
That works for me.  Thanks!

---

