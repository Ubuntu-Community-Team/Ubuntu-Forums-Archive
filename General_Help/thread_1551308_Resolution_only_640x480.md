---
title: "Resolution only 640x480"
date: 2010-08-12
forum: General Help
---

### Post by MadsRH on 2010-08-12
Hi
So everything was running fine until I wanted to fix the Plymouth boot screen with [this tutorial]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml").

I ran the **sudo apt-get install v86d** and regretted because I could not remember my TV resolution (this is for my HTPC). So I left the tutorial and when I Rebooted I only got 640x480 on my desktop!

Xrandr says max res. 640x480

Thought it might help to complete the tutorial and so I did, with the screen resolution set to 1366x768 (rather than 1280x1024 Which the Softpedia tutorial uses). No luck, no change :-(

Can any help me??

---

### Post by dino99 on 2010-08-12
actual kernel deal directly with X, so remove xorg.conf (sudo rm -f /etc/X11/xorg.conf)

check driver activation (system admin hardware driver)

---

### Post by MadsRH on 2010-08-12
Thanks for the reply> **dino99 said:**
> actual kernel deal directly with X, so remove xorg.conf (sudo rm -f /etc/X11/xorg.conf)

check driver activation (system admin hardware driver)

So I just remove the file?

The Nvidia prop. driver is active

---

### Post by realzippy on 2010-08-12
> **dino99 said:**
> actual kernel deal directly with X, so remove xorg.conf (sudo rm -f /etc/X11/xorg.conf)

check driver activation (system admin hardware driver)



Beware.
If you run a nvidia/ATI closed source driver,you need the xorg.conf !!


Edit:
When Nvidia is active,open terminal and reconfigure your xorg.conf by:

```
sudo nvidia-xconfig
```

---

### Post by MadsRH on 2010-08-12
> **realzippy said:**
> Beware.
If you run a nvidia/ATI closed source driver,you need the xorg.conf !!


Edit:
When Nvidia is active,open terminal and reconfigure your xorg.conf by:

```
sudo nvidia-xconfig
```

Fantastic! That did the trick. Thank you so much :D

---

### Post by realzippy on 2010-08-12
Fine.Please set thread as "solved" (Threadtools).

---

### Post by MadsRH on 2010-08-12
> **realzippy said:**
> Fine.Please set thread as "solved" (Threadtools).

Will do :-)

The screen seems to be flickering now! After about a minute the flickering goes crazy and I can't read anything on the screen. But the boot screen is looking nice.

---

### Post by realzippy on 2010-08-12
Hm.Open the nvidia-settings and check the refresh rate...

```
gksudo nvidia-settings
```


Which NVIDIA driver?
Maybe you can try to upgrade to "current" driver..


OFFTOPIC:
1000FRYD still exists?

---

### Post by MadsRH on 2010-08-12
Nvidia 1.7.6

Got rid of the flicker in the nvidia-settings, by setting the res to anything below 1024x768. Very strange, but it seems to work now

Thanks again

---

### Post by realzippy on 2010-08-12
Do not forget to save to xorg.conf in nvidia-settings or
settings will not persist after reboot.
So you can only use resolutions below 1024*768?
Is that satisfying?

---

### Post by DrMelon on 2010-08-12
If you have a PAL television you should set your refresh rate to 50Hz. If it's an NTSC television you should set your refresh rate to 60Hz.

---

### Post by MadsRH on 2010-08-12
> **realzippy said:**
> So you can only use resolutions below 1024*768?
Is that satisfying?

It seems that way. I hope so, but I'm not sure how it look when I connect it to the TV (which has 1366x768 as max).

---

