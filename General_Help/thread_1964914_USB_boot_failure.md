---
title: "USB boot failure"
date: 2012-04-24
forum: General Help
---

### Post by narsil4 on 2012-04-24
Burned 10.04 LTS image onto a USB stick using the 11.10 live CD per the instructions at [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Upon attempting to boot with USB, I got:

SYSLINUX 4.04 EDD 2011518 Copyright (c) 1994-2011 A Peter Anvin et al
unknown keyword in configuration file: gfxboot
vesamenu.c32: not a COM32R image

... and the last line prints again every 10 seconds or so.

I only have a 1GB stick available; the burn reported success even though the download page says a 2GB stick is needed. Am I encountering this problem because I didn't use a 2GB stick? If so then I wonder why, since the iso is 700MB.

---

### Post by JC Cheloven on 2012-04-24
Hi, at least I can tell that 1Gb usb stick should not be the problem.

It could be a bad iso image. Did you check the md5sum? ([instructions here]("https://help.ubuntu.com/community/HowToMD5SUM"))

It could be your graphics card not being supported by 10.04. What is it? This command will tell us: ```
lspci |grep VGA

```

It could be a bad usb stick. Please, from your 11.10 live cd, try to setup a live pendrive to your usb stick (yes, you can use the same cd to run a live session and to build a bootable usb key of the same system).

Anyway, just out of curiosity, have you a particular interest in 10.04? It's a bit aged by now... and if you want it lighther, there are alternatives. 

Thank you.

---

### Post by narsil4 on 2012-04-24
Thanks for the reply.

I didn't verify the checksum, and unfortunately there no way to check now since I rebooted since burning.

```
ubuntu@ubuntu:~$ lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5750 Series]
```

I was able to burn 11.10 to my USB just as you suggested, and it boots! So at least it's not the USB.

My interest in 10.04 rests only in it being different from 11.10, as I've been unable to install the latter ([http://ubuntuforums.org/showthread.php?p=11871520](http://ubuntuforums.org/showthread.php?p=11871520)).

---

### Post by JC Cheloven on 2012-04-25
> **narsil4 said:**
> My interest in 10.04 rests only in it being different from 11.10, as I've been unable to install the latter ([http://ubuntuforums.org/showthread.php?p=11871520](http://ubuntuforums.org/showthread.php?p=11871520)).

In that thread I see that you decided (a couple of hours ago) to go for 12.04, which worked for you. 
I was about suggesting you just the same thing (12.04)... but tomorrow, as it's the official release date. But you should be fine, I think your system will be exactly the same after you update it.

Glad you sorted it, and good luck!
JC

---

