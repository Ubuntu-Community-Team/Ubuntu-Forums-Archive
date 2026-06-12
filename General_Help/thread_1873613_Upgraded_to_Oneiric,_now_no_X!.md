---
title: "Upgraded to Oneiric, now no X!"
date: 2011-11-01
forum: General Help
---

### Post by mathgirl on 2011-11-01
I upgraded my Lucid machine to Meerkat without a problem.  Then from Meerkat to Natty was OK.  But now that I've updraded to Oneiric, I just get the purple Ubuntu... screen at startup and it pauses forever.  I'm able to startup in safe mode (I'm writing this in a terminal from elinks).  Also while the machine hangs at Ubuntu... I can ssh into it from another machine and look around.  So I can provide any logs and anything anybody wants.

How do I make it so I can login via gdm or whatever or rollback to Meerkat?  I love the CLI, but I can't get that much work done without being able to see PDFs, etc.  Please help!

---

### Post by Yayestechlab on 2011-11-01
Lightdm can be troublesome. You can go back to gdm, which should fix your problem. To do this first install gdm again (it is removed in the upgrade and replaced with lightdm) by running ```
sudo apt-get install gdm
```  then run ```
sudo dpkg-reconfigure lightdm 
``` and choose gdm from the list that appears.

---

### Post by mathgirl on 2011-11-02
:( I did as you said, but still get the same behavior at startup.  Just the purple ubuntu... screen.  Is there something from dmesg that would describe what's happening?

---

### Post by Yayestechlab on 2011-11-03
Try running ```
sudo apt-get --reinstall install plymouth
``` Plymouth is the startup splash screen, and that sounds like where your problem is.

---

### Post by mathgirl on 2011-11-03
As it turns out, my problem was pretty specific.  In order to get my mac to work with Ubuntu Lucid through Natty, I had the file ```
/etc/modprobe.d/blacklist-local.conf
``` containing only the line ```
blacklist nvidia_current
```.  Commenting out this line made everything work again.  I'm leaving this thread here in case somebody else who installed Ubuntu on a mac the same way runs across this problem.

---

