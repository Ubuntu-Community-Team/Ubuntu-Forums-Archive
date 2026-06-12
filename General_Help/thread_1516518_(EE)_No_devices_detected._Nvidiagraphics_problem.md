---
title: "(EE) No devices detected. Nvidia/graphics problem"
date: 2010-06-23
forum: General Help
---

### Post by vys on 2010-06-23
I'm running 64-bit Lucid on a mobile i3 core processor with 4 gb of ram and an Nvidia Geforce 310M 512MB graphics card, and an integrated Intel graphics chip I'm not sure of the specs for. I had compiz and everything working perfectly, and then I installed the Nvidia driver from ubuntu software center, and now my graphics are broken.

the computer couldn't boot, so I had to edit GRUB and delete 'quiet splash' and replace it with 'nomodeset'. then the computer would boot, but in low graphics mode, with compiz disabled and whatnot. I went to System --> Administration --> Hardware Drivers and checked what I had activated, and it said the current Nvidia one was active, so I deactivated and removed it, and the 185 one from  the software center. now with no drivers installed on my computer, I can boot, but still in low graphics mode. I went back to Hardware Drivers, and it checked for the available drivers, found the Nvidia accelerated graphics driver, and I activated it, and rebooted. this resulted in the splash screen being broken again so I deactivated it again, and now I'm stuck. The reason my computer gives for booting in low graphics mode is that "(EE) No devices detected".

I willing to use either graphics card on Linux because I'm not playing games, so can someone tell me how to straighten out the graphics?

---

### Post by VH-BIL on 2010-06-23
**First you can download the nvidia driver from:**
[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

**Then install it in Lucid using this tutorial:**
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

**If you want to get the boot plymouth working again:**
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by vys on 2010-06-23
so I followed all the instructions, but it said that the distributor-provided pre-install scripts failed, but I had the option of continuing anyway, so I did. I rebooted, and it still went into low graphics mode, saying that no devices were detected.

---

### Post by VH-BIL on 2010-06-23
> **vys said:**
> so I followed all the instructions, but it said that the distributor-provided pre-install scripts failed, but I had the option of continuing anyway, so I did. I rebooted, and it still went into low graphics mode, saying that no devices were detected.

Did you blacklist:
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```

Did you:
```
sudo apt-get --purge remove nvidia-*
```

did you reboot before installing?

---

### Post by vys on 2010-06-23
yeah, I'm gonna do a fresh install and see what happens. my installation was only like two days old.

---

### Post by VH-BIL on 2010-06-24
I don't have a lot of experience with the 64bit edition.

---

### Post by vys on 2010-06-24
after the fresh install, everything works, and Hardware Drivers tells me that I don't have any drivers installed on my system. which is perfectly fine if it works, so I'm not messing with it any more. thanks for your help.

---

### Post by VH-BIL on 2010-06-24
Glad everything is working for you :)

---

