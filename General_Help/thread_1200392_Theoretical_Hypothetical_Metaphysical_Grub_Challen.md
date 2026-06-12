---
title: "Theoretical Hypothetical Metaphysical Grub Challenge"
date: 2009-06-30
forum: General Help
---

### Post by Megrimn on 2009-06-30
**So here's the hypothetical [solved] situation:** 

The CD drive on my Compaq Presario 1200 doesn't work.  I installed ubuntu earlier by removing the HDD and installing with a different computer.  

I would like to re-install.  So. I created a USB live CD.  But the bootloader on the computer is old and won't boot from USB.  What I want to do is create an entry in /boot/grub/menu.lst that could boot the USB drive and so start the live CD which is on the USB drive.  

Does anyone have a theoretical or tried-and-true entry I could use in menu.lst to boot the USB live CD from grub?

Thanks in advance, once again.

---

### Post by synapsys on 2009-06-30
[http://ubuntuforums.org/archive/index.php/t-992426.html](http://ubuntuforums.org/archive/index.php/t-992426.html)

---

### Post by Megrimn on 2009-06-30
> **synapsys said:**
> [http://ubuntuforums.org/archive/index.php/t-992426.html](http://ubuntuforums.org/archive/index.php/t-992426.html)

nice, we'll see if that works.

[edit] thanks buddy, it did work.

---

### Post by Megrimn on 2009-07-01
right, so here is the grub entry I ended up using, from the above link plus some other scrounging around:

```

   title Run Ubuntu 9.04 from USB DISK
   root (hd0,0) 
   kernel      /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash ignore_uuid xforcevesa
   initrd      /casper/initrd.gz
```

I found this link by following another link in the previous post, and that's how I got the 'ignore_uuid' option that helped it not boot into the 'Busybox' thing: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Then this link had another helpful option, 'xforcevesa'.  On my computer the boot process doesn't go any further than the splash screen unless it uses the VESA driver, because the graphics card is an old piece of junk (and is built into the motherboard :()
:[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Of course, you can do this with any distro: just change 'ubuntu.seed' to whatever you want, ex. kubuntu.seed or xubuntu.seed.   Wouldn't be a bad idea to change the title, either; it isn't necessary, but less likely chance of a screw-up. I was doing it with Kubuntu.

---

