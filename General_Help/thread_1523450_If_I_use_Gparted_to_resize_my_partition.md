---
title: "If I use Gparted to resize my partition?"
date: 2010-07-03
forum: General Help
---

### Post by BigCityCat on 2010-07-03
I have done this before and lost my boot screen. Is there an easy way to resize that partition? I know the graphical interface allows you to just slide it one way or the other but I did that in the past and I had a boot error. Can I just update grub before I reboot? Is that enough?

---

### Post by Masterj15 on 2010-07-03
how new is your computer? it could be a bios thing (not being able to handle a certain space so it affectz the grub)

---

### Post by BigCityCat on 2010-07-03
It's pretty new 64bit 250 gigs dual core 4 gigs ram. I see you can slide the windows partition to shrink it. I assume you could just enlarge ubuntu after that but the last time I had a boot error. I guess the mbr was moved and could not be found.

---

### Post by Mark Phelps on 2010-07-03
Oh oh -- you said "windows partition" ...

Do you mean Windows as in MS Windows?

IF so, and your MS Windows is Vista or Win7, do NOT use GParted to shrink it.  Doing so is likely to damage it and render it unbootable.

IF it's Windows XP. you should be OK.

---

### Post by wilee-nilee on 2010-07-03
The loss of boot I think is a grub-legacy problem. Your still using Jaunty which is probably G-L.

Run this command to confirm grub type.
```
sudo grub-install -v
```

If it shows grub.97 then you may consider upgrading to grub2 it is different but more auto friendly for resizing and editable if needed in the manner used with grub2.

Here is a link, this is a straightforward process, but you have to do every command correctly and in the order described, which includes commands after installing and rebooting.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

If you do this and everything else is in order boot wise and you use the W7 disc manager for W7 resizing and gparted from a live cd for the Ubuntu changes, you should be fine. Grub2 should boot automatically after resizing.

---

### Post by jwbrase on 2010-07-03
> **BigCityCat said:**
> I have done this before and lost my boot screen. Is there an easy way to resize that partition? I know the graphical interface allows you to just slide it one way or the other but I did that in the past and I had a boot error. Can I just update grub before I reboot? Is that enough?

I did a resize maybe six months ago (also with Jaunty and Grub legacy) and I can confirm that it did mess up grub, but I was able to fix it in a jiffy.

---

### Post by nmaster on 2010-07-03
> **Mark Phelps said:**
> Oh oh -- you said "windows partition" ...

Do you mean Windows as in MS Windows?

IF so, and your MS Windows is Vista or Win7, do NOT use GParted to shrink it.  Doing so is likely to damage it and render it unbootable.

IF it's Windows XP. you should be OK.

actually there is a way to fix vista after using gparted. check out # 9: [http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

