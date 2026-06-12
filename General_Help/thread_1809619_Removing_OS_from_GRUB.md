---
title: "Removing OS from GRUB"
date: 2011-07-21
forum: General Help
---

### Post by DugMatt77 on 2011-07-21
Hi. When I start my computer, the Windows boot loader comes up first and is promptly replaced by the grub boot loader. I have two questions.

Firstly, how do I make the windows boot loader primary so that the GRUB boot loader doesn't show at all? And will I still be able to boot Ubuntu 10.10 from the windows boot loader if I choose to change it back?

Secondly, if the above is not possible, when GRUB boot loader appears, It had about 7 options to choose from:

Ubuntu, with Linux 2.6.38-10-generic
Ubuntu, with Linus 2.6.38-10-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serioual console 115200)
Windows Vista (loader) (on /dev/sda3)
Microsoft Windows XP Embedded (on /dev/sda5)

Can I reduce this to just the 2 options? Or am I best to just leave it alone?

Thanks!
ps. im a computer newbie! I know nothing! This is all because of my older bros trial and error experiment on my laptop and now hes gone!

---

### Post by waveOSBeta on 2011-07-21
I suggest installing GRUB customizer. Also, have you looked into [BURG](http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/)?

---

### Post by DugMatt77 on 2011-07-21
So in the GRUB boot loader, are all the options provided, bar Windows Vista and Ubuntu Generic, actually essential? If I remove them, my computer won't have any problems?

---

### Post by waveOSBeta on 2011-07-21
With GRUB customizer, you can hide them without removing them. I suggest you keep the latest Ubuntu, the latest Ubuntu safe mode, and windows. I, for one, prefer BURG. It's pretty. :P

---

### Post by DugMatt77 on 2011-07-21
Yeah sounds pretty sweet. Just as a matter of interest, does your computer automatically run windows boot loader for 2 seconds before being over-ridden by the GRUB boot loader?

---

### Post by DugMatt77 on 2011-07-21
Also, how do I figure out what drive (hd) to add the grub customizer to?

---

### Post by waveOSBeta on 2011-07-21
Default works fine for me. :)

---

### Post by DugMatt77 on 2011-07-22
But when I get up to here...:

```
matty@MasterShifu:~$ sudo burg-install (hd0)
bash: syntax error near unexpected token `('

```

---

### Post by Quackers on 2011-07-22
Turn off the memtest entries with ```
sudo chmod -x /etc/grub.d/20_memtest86+
```

---

### Post by waveOSBeta on 2011-07-22
> **DugMatt77 said:**
> Also, how do I figure out what drive (hd) to add the grub customizer to?
Try sda0. You installed customizer yet?

---

### Post by Mark Phelps on 2011-07-23
Just in case anyone suggests it ... do NOT use startup-manager.  It does NOT know how to handle the new nested menus.  I know, I've been using it for some time and recently discovered that it no longer works properly with the new GRUB nested menus.

---

