---
title: "FGLRX - Will it break my system (again)."
date: 2011-04-24
forum: General Help
---

### Post by yanom on 2011-04-24
So a few weeks ago, I was running Ubuntu/Windows7 Dual Boot, and I installed the proprietary FGLRX ATI graphics card driver. This rendered my Ubuntu system command-line only, and I had to install all over again. If I install FGLRX now, will this happen again or has the bug been fixed? If it does happen again, is there any way to revert to the open-source ATI driver from the command line?

---

### Post by yanom on 2011-04-25
Bump.

---

### Post by dino99 on 2011-04-25
if you have a xorg.conf, better to remove it:

sudo rm /etc/X11/xorg.conf

to install the radeon driver:

sudo apt-get install xserver-xorg-video-radeon

---

### Post by cottfcfan on 2011-04-25
What graphics card do you have?

---

### Post by hawthornso23 on 2011-04-25
[LIST=1]
[*]What is your graphics hardware?

Be aware that older ATI graphics cards don't work with the newer versions of XOrg. Trying to enable a proprietary driver if you have an older card will hose your GUI.
[*]How are you installing fglrx?

The safest way is via System>administration>hardware drivers
[/LIST]

---

### Post by coffeecat on 2011-04-25
> **yanom said:**
> If I install FGLRX now, will this happen again or has the bug been fixed? If it does happen again, is there any way to revert to the open-source ATI driver from the command line?

One for your bookmarks:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Couple of questions. Which, exactly, is your ATI card? Were you getting acceptable performance with the open source ati driver?

---

### Post by yanom on 2011-04-25
My ATI card is brand-new. ATI Radeon 5xxx I THINK. Not at home ATM. Anyway, the driver is fglrx, not radeon. The Open-source driver gives me trouble on some 3-d programs, namely Minecraft.

Anyway, why should I remove my Xorg.conf? Isnt that what controls the entire X Window System?

---

### Post by yanom on 2011-04-25
> **hawthornso23 said:**
> [LIST=1]
[*]What is your graphics hardware?

Be aware that older ATI graphics cards don't work with the newer versions of XOrg. Trying to enable a proprietary driver if you have an older card will hose your GUI.
[*]How are you installing fglrx?

The safest way is via System>administration>hardware drivers
[/LIST]

Also, yes, I am installing it that way.

---

### Post by cottfcfan on 2011-04-26
Try following carefully the guide here:
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Although reading on the Phoronix website, AMD support for your graphics card is still quite buggy.

---

### Post by yanom on 2011-04-26
ok, once I install the driver, how do I revert to the Open-Source ATI driver if FGLRX doesn't work right?

---

### Post by coffeecat on 2011-04-26
> **yanom said:**
> ok, once I install the driver, how do I revert to the Open-Source ATI driver if FGLRX doesn't work right?

Already answered. See the link in my post #6.

---

### Post by yanom on 2011-04-26
ok, reinstall thoses "ati" packages and it sets itself up just fine?

---

