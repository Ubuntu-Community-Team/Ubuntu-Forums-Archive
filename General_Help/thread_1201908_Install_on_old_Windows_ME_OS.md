---
title: "Install on old Windows ME OS"
date: 2009-07-01
forum: General Help
---

### Post by Fritzili on 2009-07-01
I would like to install a version of Ubuntu on an older PC that currently has Windows ME operating system installed. The processor is a 900 mhz AMD Duron with 128 kbtes of RAM memory. Is there an older version that might work with this ancient machine? If so, where do I get a copy. Thanks,

Fritzili

---

### Post by oldfred on 2009-07-01
I have an old portable with only 128kb and it took over 10 hours to install Xubuntu and another 10 to do all the updates. I was surprised it even worked. It was still slow running. I installed Puppy, which was much faster both to install and use but it did not work with my USB Ethernet dongle. I ended up with Zenwalk which had a newer Linux version that worked with my USB port and was reasonably fast. There are other small Linux distros but you need to make sure they say they will work with only 128k. If you can add memory I would do that since it is so cheap now.

---

### Post by Chronon on 2009-07-01
Fritzili: You can't boot Windows ME with 128KB of RAM.  You must mean 128MB.

oldfred: I think you're confused as well, since no computers with 128K of RAM ever had a USB port.  Here's an old portable with 128KB of RAM: [http://oldcomputers.net/compaqi.html](http://oldcomputers.net/compaqi.html)

;)

==
Sorry, that comes off a bit snarky as I pointed out a notation error and didn't offer any advice.  Here's an article with some suggested distributions for lower powered hardware: [http://www.linux.com/archive/articles/52134](http://www.linux.com/archive/articles/52134)

---

### Post by t4thfavor on 2009-07-01
I ran 8.10 xubuntu on a pIII 600 with 128mb ram. It worked OK. Not that it was snappy or anything, just usable. 

I upgraded it to 1gb of ram and it works pretty quick now. 128mb was a pretty good thin client, and a moderate workstation.

I would install server on it, and then play around with a gui-less system for a while it would be pretty fast w/o a gui.

---

### Post by DGortze380 on 2009-07-01
My typical suggestion, DSL (Damn Small Linux).

There are Linux Distros meant to run on machines with older hardware similar to yours. 

It's not a good idea to run an old version of Linux just because the machine is old ... these unsupported version don't get critical security updates. Instead use a 'lightweight' distro like DSL, Puppy Linux, or Xubuntu (IMO Xubuntu is a little heavy for your system, but you can decide for yourself).

---

### Post by t0p on 2009-07-01
> **Fritzili said:**
> I would like to install a version of Ubuntu on an older PC that currently has Windows ME operating system installed. The processor is a 900 mhz AMD Duron with 128 kbtes of RAM memory. Is there an older version that might work with this ancient machine? If so, where do I get a copy. Thanks,


Don't install an old version of Ubuntu!  It'd be out-dated and unsupported, which would certainly be an issue security-wise!

Ubuntu won't run properly on just 128 MB of RAM (you did mean 128 MB didn't you?).  I'm not sure if Xubuntu would work okay with such little RAM.  There are smaller, lighter Linux distros to choose from: google for **Damn Small Linux** and **Puppy Linux**.  There are also lighter window managers, that you could possibly run with Ubuntu to work on your machine: google **LWM**, **Fluxbox**, and also **midnight commander**.  If you installed, say, Damn Small Linux with the Fluxbox window manager, you'd have a small, light, fast modern Linux.

---

