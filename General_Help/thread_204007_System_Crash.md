---
title: "System Crash"
date: 2006-06-26
forum: General Help
---

### Post by atul_dapper on 2006-06-26
Hi,

Any helpful advise towards recovery is appreciated.

Chronlogy of events:

- Dapper worked great for a month or so on Inspiron 7500 Laptop, simply a SUPERB very addictive installation!!  Used daily for about 4-5 hours.

- Today (June 26, 2006)
1.  In Terminal, executed usplash.  
    (Other running apps at the time: noatun, firefox, synaptic, citrix ICA.
2.  System went into "hang" state and no keys worked
3.  Did a hard shutdown, by holding down the power button
4.  During re-boot, went into recovery mode and executed fsck
5.  fsck gave many many errors, about inode and many others, went on answering yes/Y to all, gave up and hard rebooted 
6.  Next reboot gives error on any/all the options in GRUB:
    * INIT: version 2.86 booting
    * INIT: No inittab file found
sulogin : cannot open password database!

Enter runlevel :

7.  If any runlevel is entered, like 0,1,S, etc,:
     * INIT: Entering runlevel : 0
     * INIT: no more processes left in this runlevel


How can I recover the installation; if not atleast the files.

Thanks and regards.
A/Dapper.

---

### Post by rbalfour on 2006-06-26
Sounds like a bad hard disk. anyway, you can try booting with the LiveCD and mount the hard and cooy the home directory.

---

### Post by atul_dapper on 2006-06-27
Thank you for the suggestion.

I did what you said, and was able to mount and recover the home directory.

Found out that the /etc had completely vanished, could not fix this.  Just reformatted.

(Further unfortunately, I only have the Kubuntu discs, and when I installed that KUBUNTU, I just cannot bear to look at it or work with it after working with Ubuntu for more than a monht now...sorry just not for me, have to dump it.)

Also, does anyone know how to get UBUNUTU CDs shipped, and not KUBUNTU.  Where do I state explicitly that I need UBUNTU CDs and NOT KUBUNTU or something else.

Sorry!

---

### Post by PriceChild on 2006-06-27
You could always just install kubuntu, then install gnome-desktop and remove any kubuntu packages you don't want to?

---

