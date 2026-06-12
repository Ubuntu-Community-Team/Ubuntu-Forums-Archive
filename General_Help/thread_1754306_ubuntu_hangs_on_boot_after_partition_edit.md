---
title: "ubuntu hangs on boot after partition edit"
date: 2011-05-09
forum: General Help
---

### Post by beezum88@gmail.com on 2011-05-09
Ok, so I've been messing around with my HD partitions lately, deleting some OSes I don't use to make room for data. Before the last partition edit, I had Win7, Ubuntu Lucid, openSUSE 11.4, and VectorLinux in a quad-boot situation. Everything worked fine (except, for some reason, hibernate, on any OS). I deleted the VectorLinux install and resized my data partition. I touched nothing else. Now, openSUSE and Win7 have no problems, but Ubuntu hangs on startup.

Here's what happens:
I turn on the computer
GRUB comes up
I choose Ubuntu
The Ubuntu boot screen (with the Ubuntu logo and the five red dots beneath) comes up.
All the dots turn red.
Absolutely nothing else happens.
I tap the power button.
Ubuntu interrupts whatever it's doing and shuts down normally
Computer turns off.


I tried booting into recovery mode, and it works, but I get the command line and don't know what I need to fix to get the regular mode to boot.

Anyone have suggestions?

Thanks!

---

### Post by lmarmisa on 2011-05-09
Boot into Ubuntu recovery mode and type these commands (I suppose you will have root privileges):

```

update-grub
reboot

```

If you do not get any success, boot your system into openSUSE, run the Boot Info Script and post here the results:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by beezum88@gmail.com on 2011-05-09
Well, I just tried again and it has apparently magically healed itself. I guess I'll never know what the problem was, now. Thanks for the suggestions, though.

---

### Post by lmarmisa on 2011-05-09
You are very lucky. Computer problems solved by themselves are extremely infrequent. :D

Best regards,

Luis

---

