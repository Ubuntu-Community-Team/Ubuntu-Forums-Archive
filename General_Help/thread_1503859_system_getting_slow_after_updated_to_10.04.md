---
title: "system getting slow after updated to 10.04"
date: 2010-06-07
forum: General Help
---

### Post by yilin on 2010-06-07
I noticed that my laptop getting slower after updated to ubuntu 10.04.
Application windows often turn to grey and the system stop responding until the greyness was gone.

I don't think I was running any big jobs. And this could happen to any application.

What cause this? Thanks for your help.

---

### Post by arubislander on 2010-06-07
> **yilin said:**
> I noticed that my laptop getting slower after updated to ubuntu 10.04.
Application windows often turn to grey and the system stop responding until the greyness was gone.

I don't think I was running any big jobs. And this could happen to any application.

What cause this? Thanks for your help.

Do you notice any increase in CPU usage when the windows gray? What type of graphics card do you have on your laptop?

---

### Post by kleskjr on 2010-06-07
was it upgrade or a fresh install?
most users do a fresh install to avoid similar problems

---

### Post by loefaas on 2010-06-07
This has happened to more people (I am one of them) see for example [http://ubuntuforums.org/showthread.php?p=9285497](http://ubuntuforums.org/showthread.php?p=9285497).

I have tried in different forums but none seems to now what the problem is. My guess is that is a severe memory bug in 10.04, probably something with Xorg in combination with intel graphics drivers. Since there is no word from the crew, either they don't care about it or it is a BIG problem.. Seems like the only solution is to go back to 9.10.

---

### Post by drascus on 2010-06-07
I would agree with what someone else said. this could have resulted from upgrading rather then doing a fresh install. have you tried not using the proprietary driver if any? or using a different driver for your video card. As to "the crew" they probably just don't have a computer with your configuration so it's kind of hard for them to test and figure out just what went wrong.

---

### Post by loefaas on 2010-06-07
Maybe my answer was a little harsh, but there have been several bug reports submitted with full hardware spec. etc, see for example [https://answers.launchpad.net/ubuntu/+question/112151](https://answers.launchpad.net/ubuntu/+question/112151) 
And I haven't found any real answer yet, only people with the same trouble.

Is it too much to demand that when you put out a LTS-version it is not worse than the previous one? Maybe the aim for 10.04 was a little to high? some functions maybe should have waited for 10.10 and made 10.04 a long term stable version?

---

### Post by yilin on 2010-06-07
The hardware: Latitude D630 Intel(R) Core 2 Duo 2.2Gh
Memory 2 GB

Kernel Linux 2.6.32-22-generic

GNOME 2.30.0

When some app getting grey (Evolution or Firefox typically), my System Monitor shows 14% cpu usage and the memory usage is around 30% of 2GB
But the monitor itself is not respondinng:(

Anyway, I tend to say there are some bugs.

Ubuntu is somehow getting close to windows not only for the looking but also for the performance?

---

### Post by themarker0 on 2010-06-07
> **yilin said:**
> The hardware: Latitude D630 Intel(R) Core 2 Duo 2.2Gh
Memory 2 GB

Kernel Linux 2.6.32-22-generic

GNOME 2.30.0

When some app getting grey (Evolution or Firefox typically), my System Monitor shows 14% cpu usage and the memory usage is around 30% of 2GB
But the monitor itself is not respondinng:(

Anyway, I tend to say there are some bugs.

Ubuntu is somehow getting close to windows not only for the looking but also for the performance?

I hate to say it, but try a fresh install, on a new partition. If it works fine, its the upgrade. If it doesn't work, its lucid not liking your laptop, and you'll have to move down to 9.10

---

### Post by yilin on 2010-06-16
My system is part of tripple boot. I don't like to go through complicated full install unless there is no otherways.

I tried the game Quadrapassel. It's not playable anymore. I'm wondering if it can be reasonablly run on a fresh installation.

---

### Post by loefaas on 2010-06-16
> **yilin said:**
> My system is part of tripple boot. I don't like to go through complicated full install unless there is no otherways.

I tried the game Quadrapassel. It's not playable anymore. I'm wondering if it can be reasonablly run on a fresh installation.

I have partly solved the problem for me. It seems that is some problem with new kernel and load balancing for Intel core processors. For me 10.04, is running equal to 9.10, if I use the karmic kernel (2.6.31) with lucid.

---

### Post by K.J. on 2010-06-16
It's almost certainly because you did an upgrade instead of a fresh install.  You can try deleting the .gnome* folders in your home directory and rebooting. See if things run better for you.

Otherwise, backup your grub file and reinstalling shouldn't break your triple boot setup.

---

### Post by yilin on 2010-06-16
yes I tried the back kernel, much fast! I don't know if all the new version features is available with older kernels

---

### Post by yilin on 2010-06-17
2.6.31-21-generic runs ok without notable slowness,
2.6.31-22 is very slow.

Does this still leave the possibility of a fresh install will solve the problem?

---

