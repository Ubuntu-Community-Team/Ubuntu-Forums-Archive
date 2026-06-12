---
title: "Ubuntu 10.04 on Toshiba Satellite"
date: 2010-05-09
forum: General Help
---

### Post by BluBird on 2010-05-09
Not a hardcore ubuntu user, so please bear with me. I have dell B130 with Ubuntu Karmic on it, and I like it. I recently purchased a new laptop, a Toshiba Satellite A505-S6033. I've been trying for about 24 hours to get Ubuntu 10.04 64 bit on this computer, but to no avail. I've seen some people say that they get error messages. When the cd loads up, it comes to the main page (run ubuntu off disk, install ubuntu, check for errors, etc.) Anyway, when I click to run it off the disk, the scren goes blank. The CD spins, but nothing happens from then on. I've tried a 32 bit version of Ubuntu 10.04, but the same thing happens. Just for experimentation, I tried xPud on it, and xpud works fine. Does anyone have any ideas? Thanks!
-Karl

---

### Post by Catharsis on 2010-05-09
Try enabling "nomodeset". From the LiveCD menu, make sure "Try Ubuntu without making changes" is selected and then hit F6 and then select "nomodeset". Then hit Enter.

Edit: How long have you let it wait? Try booting into the LiveCD and wait until the CD stops spinning. It might just be taking a while to load; it's a CD after all.

---

### Post by tomcatjosh on 2010-05-10
I Have an A55. Same Problem, And The CD Spins down too.

---

### Post by skippuff54 on 2010-05-19
I had a similar issue a year or so ago when I first installed Ubuntu.

I ended up installing over the network using an ethernet cable plugged into my wireless router. 

You may first want to try using the Alternate (text-based) install CD image or the Minimal CD image.

So that is a total of four methods that I tried before getting everything set up - LiveCD, Alternate CD, Minimal CD, Network install (via wired network).

My issue was that the installer would hang when it got to the xorg segment.

---

### Post by acepelon on 2010-08-01
This is a common problem.  I have an A505 as well.  This works:

[http://ubuntuforums.org/showthread.php?t=1400432&page=6](http://ubuntuforums.org/showthread.php?t=1400432&page=6)

Use the AMD64 version of the iso to get 64-bit processing.  Even though it says AMD, it works fine.

Then you will have to fix the wireless networking which I am in the process of hammering out, but there are posts all over the forums about it.

Good luck

---

### Post by Catharsis on 2010-08-01
> **acepelon said:**
> This is a common problem.  I have an A505 as well.  This works:

[http://ubuntuforums.org/showthread.php?t=1400432&page=6](http://ubuntuforums.org/showthread.php?t=1400432&page=6)

Use the AMD64 version of the iso to get 64-bit processing.  Even though it says AMD, it works fine.

Then you will have to fix the wireless networking which I am in the process of hammering out, but there are posts all over the forums about it.

Good luck

Please don't use that fix. That is not the right way to add options to GRUB. Instead, just:
```
gksudo gedit /etc/default/grub
```
And then append them to the "GRUB_CMDLINE_LINUX_DEFAULT" line. Then run:
```
sudo update-grub
```

But regardless, that fix won't work because KMS is already disable in Lucid for i8xx cards. For the correct workarounds, please see:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

