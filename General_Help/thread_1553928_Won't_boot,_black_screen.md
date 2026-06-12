---
title: "Won't boot, black screen"
date: 2010-08-15
forum: General Help
---

### Post by Twizlerr on 2010-08-15
I was just doing some web browsing, and I was on a website with a ton of script (djearworm.com). I got really impatient because I was getting error messages and it asked me to force quit (didn't work), so I just held down the power button so I could restart.

Well, I can get to grub, but if I boot, it gets stuck. Here's exactly what happens: It does the thing where it has the flashing underscore in the top left corner. Then I see the purple screen and the orange dots and all. After that I see flashing text for a couple seconds. Then the screen goes black (still lit up though). The text I see looks like this:
```
Ubuntu 10.04 LTS ubuntu ttyl
ubuntu login:
```
it flashes maybe 4 or 5 times, then disappears. I'm able to select recovery mode, but I have no idea what to do after that :\

Can anyone please help? Thanks in advance

---

### Post by wilee-nilee on 2010-08-15
Try the recovery boot choose normal boot and if it drops you to a login, then login and then run startx.

Theoretically nothing should have happened to your boot from what you describe but I don't know what you were doing or even what type of install this is, I.E. wubi, or dual boot or a single install.

If nothing works post the bootscript in my signature in code tags as described.

Was this a hard shutdown of Ubuntu running in wubi?

---

### Post by Twizlerr on 2010-08-15
> **wilee-nilee said:**
> Try the recovery boot choose normal boot and if it drops you to a login, then login and then run startx.

Theoretically nothing should have happened to your boot from what you describe but I don't know what you were doing or even what type of install this is, I.E. wubi, or dual boot or a single install.

If nothing works post the bootscript in my signature in code tags as described.

Was this a hard shutdown of Ubuntu running in wubi?

I'm running a dual boot that I installed with Wubi. When I shut down, I held the power button until the computer shut down.

```
(EE) PSB(0): screnIndex is:0;fbPhys is:0x3f800000; fbsize is 0x007bf000
xf86TokenToOptinfo: table is NULL
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
FATAL: Module psb not found.
(EE) [drm] drmOpen failed.
(EE) PSB(0): [dri] DRIScreenInit failed. Disabling DRI.
(EE) [drm] Could not uninstall irq handler.
(EE) PSB(0): This driver currently needs DRM to operate.

Fatal server error:
AddScreen/ScreenInit failed for driver 0

Please consult the The X.Org Foundation support at http://wiki.x.org for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

ddxSigGiveUp: Closing log
giving up
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errorno 3): Server error.
```*pant*
that took forever... I had to type all of that on my iPhone :\

---

### Post by wilee-nilee on 2010-08-15
There are a few users on the forum that are familiar with wubi and hard shutdowns. Hopefully one of them will see your post.

---

### Post by Twizlerr on 2010-08-15
> **wilee-nilee said:**
> There are a few users on the forum that are familiar with wubi and hard shutdowns. Hopefully one of them will see your post.
Okay, well, thanks for the reply. Hopefully one of those users will come across my post.

---

### Post by wilee-nilee on 2010-08-16
I looked at the Wubi guide in this section linked ntfs corrupted, if you have a install disc you can run a chkdsk.
[https://wiki.ubuntu.com/WubiGuide#Corrupted%20NTFS%20filesystem](https://wiki.ubuntu.com/WubiGuide#Corrupted%20NTFS%20filesystem)

If you don't have a disc here is a link to a legit ISO to burn.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

Instructions for chkdsk.
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

---

### Post by Twizlerr on 2010-08-16
I guess I'll check those out. Though, what I was thinking, was I should just reinstall Ubuntu. The only problem is, I have many files I would like to keep, and they are on my Ubuntu install.

Is there a way I can access those files, so I can save them on XP and then reinstall Ubuntu?

Edit: I found a program to access the Wubi-installed Ubuntu files, and copied my entire home folder to my desktop. I'll probably just do a reinstall now.

---

