---
title: "black screen in lucid (10.04) after patch update"
date: 2010-09-02
forum: General Help
---

### Post by sf_basilix on 2010-09-02
Yesterday, 9/1/2010, I received a bunch of patch updates for 10.04 (64-bit) and applied them to my laptop (Dell Latitude E6510, Intel Core i5). After they applied, it asked me if I wanted to reboot now or later. I chose later to finish my work and then shut my laptop off. This morning, I turned it on, only to get a black screen during bootup and also during login. I know it's working behind the scenes because I can hear the drum sound when it's ready to login and I can still press the power button and hit enter to shut it down. I tried using Alt+F2->F12 but it would only show a black screen.

My temporary workaround was to hold the shift button during startup to get the grub menu and then select the older 2.6.32-23 kernel to bootup instead of the newer 2.6.32-24. I am able to boot ok in the older kernel and it's working fine, but I don't know what is causing the problem for the newer one and cannot boot into that one.

I believe I was running 2.6.32-24 fine up until I received a bundle of patches to apply to my system. So the question is, is there a way to figure out what patches were applied in yesterday's bundle so I can back them out?  If not, how can I fix this so I can run the newer updated kernel?

Thanks!

---

### Post by 2New on 2010-09-02
Did a bit of googling, hope this helps:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by sf_basilix on 2010-09-02
Thanks for the quick reply. Unfortunately I tried those options and they still did not work. I do not believe it was a driver for the video adapter as I had also pressed the ALT+F keys to get to a shell prompt, but with no success. In addition, I also remember looking at the patches and I don't recall there being any video drivers in that list.  Nevertheless, I tried it anyway and my screen was still black.

Any other thoughts?

---

### Post by Stefanie on 2010-09-03
It's a known bug for the e6510. it also occurs on the e6410 but apparently the fixes are different. for the moment you should use an earlier kernel version, and try to comment on as many bug reports as possible in order to get this fixed for Maverick (the problem's still present in maverick beta!). 

[https://bugs.freedesktop.org/show_bug.cgi?id=29278](https://bugs.freedesktop.org/show_bug.cgi?id=29278)

[https://bugs.launchpad.net/bugs/561802](https://bugs.launchpad.net/bugs/561802)

---

### Post by sf_basilix on 2010-09-08
I'm looking for some guidance on how to install a mainline kernel. I opened a ticket for this here:
[https://bugs.launchpad.net/ubuntu/+bug/628986](https://bugs.launchpad.net/ubuntu/+bug/628986)

But they suggested I download the mainline kernels here:
[https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

When I go there, it explains what to download if you have 32 bit intel or AMD 64 bit, but does anyone know what I should download if I need an x86_64 (64bit 10.04 lucid) kernel?  Is it i386? Won't that just be 32 bits?

Looking for some advice - thanks!

Maybe I'll post this elsewhere where there are kernel developers also.

---

