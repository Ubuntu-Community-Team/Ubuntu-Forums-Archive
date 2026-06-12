---
title: "Ubuntu Desktop vs Lubuntu"
date: 2011-11-09
forum: General Help
---

### Post by weese on 2011-11-09
OK, so I have been running the plain Ubuntu desktop 11.10 on my Asus EEPC netbook. I saw Lubuntu on a PC Week slide show and it talked about how it was much lighter on resources and a better choice on machines with less horsepower. I downloaded and ran it on my netbook, and Lubuntu seems to use more memory than the plain vanilla install. On Lubuntu, I have a terminal open running top, and chrome opened up. On the desktop version, I also have a terminal running top and firefox loaded up. The Lubuntu distro seemed to be using MORE memory than the regular desktop version. Please help me understand what is going on here.

---

### Post by ac_d600 on 2011-11-09
Are you running Lubuntu off of a USB stick or a disk, or did you install it
on you netbook? Running off of a USB will use alot more memory than if you
have it installed.

---

### Post by Rodney9 on 2011-11-09
Are you running the live CD or is it installed ?

On my desktop I can have open half a dozen tabs in Chromium, Claws Mail, Synaptic, Gimp, Zim, Calibre, Libre Writer, Terminal all open and have Radio Tray playing all at the same time and this only uses 15% of memory and 4% of CPU

On my Laptop I can have open half a dozen tabs in Chromium, Claws Mail, Synaptic, Abiword and terminal, this uses 15% memory, 8% cpu

For more Information, How To's and Screen-Casts on Lubuntu go to [http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

Rodney

---

### Post by Seb71 on 2011-11-09
> **Rodney9 said:**
> 
On my desktop I can have open half a dozen tabs in Chromium, Claws Mail, Synaptic, Gimp, Zim, Calibre, Libre Writer, Terminal all open and have Radio Tray playing all at the same time and this only uses 15% of memory and 4% of CPU

I do not know how relevant is that, because if you have the configuration from your signature (Asus P5Q Pro MB, Intel Core 2 Duo CPU E8400 3.00GHz GSkill DDR2 8Gig Ram, Asus 9600GT Video), your desktop is capable tu use any Ubuntu variant. It is much more powerful than an Asus EEE PC netbook (which has a slower CPU and at most 2GB of RAM, but the versions shipped with Windows 7 are restricted to 1GB of RAM).

---

### Post by weese on 2011-11-09
Re: Ubuntu Desktop vs Lubuntu
Are you running Lubuntu off of a USB stick or a disk, or did you install it
on you netbook? Running off of a USB will use alot more memory than if you
have it installed. 

I am running the desktop version off my hd and the Lubuntu off of a usb stick. So why does running off of a stick use more memory. What if I installed it and ran it from an SD card. Would that be the same as running from a ssd?

---

### Post by Rodney9 on 2011-11-09
Transfer rates for usb2.0 run at 480Mbits/seconds whlie sata2 are up to 3.0 Gigabits/seconds, about 6 time faster.


Rodney

---

### Post by weese on 2011-11-09
> **Rodney9 said:**
> Transfer rates for usb2.0 run at 480Mbits/seconds whlie sata2 are up to 3.0 Gigabits/seconds, about 6 time faster.


Rodney

I am both a hardware and software engineer, so I am fully aware of the speed differences. I am trying to understand why there would be more memory use when running from a usb stick. I would also like to know if actually installing to an SD card rather than running in the "try it out" mode would would yield resource allocation numbers that are the same as running from a hard drive.
Thanks for the info.

---

### Post by 11jmb on 2011-11-09
I don't think that it has anything to do with data transfer rates, which should affect overall latency, but not memory usage.

The excess memory usage is probably from the livecd's usage of ram disks

---

### Post by weese on 2011-11-09
> **11jmb said:**
> I don't think that it has anything to do with data transfer rates, which should affect overall latency, but not memory usage.

The excess memory usage is probably from the livecd's usage of ram disks

Didn't think about the ram disks. I'll have to try it out again tonight. Thanks for the quick responses.

---

### Post by amjjawad on 2011-11-09
Hello and Welcome to Ubuntu Forum and thanks for choosing Lubuntu :)

Being a Hardware and Software Engineer, will make it easier for us to communicate because I'm sure you will understand what I'm talking about.

[B]Installing Lubuntu on a Hard Disk Drive will give the maximum speed + less memory usage.

[/B]Other than the above statement, speed could be slower and memory usage could be more.

I've been around for two years now. I have downloaded and installed more than 60 Linux Distributions. I do have now many LXDE Distributions installed because I'm doing many tests on daily basis. NOT even once, I've noticed that any LXDE Distribution will use more memory than any other distribution with another DE rather than LXDE, period. Even when trying form LiveCD or LiveUSB, LXDE Distributions didn't require so much RAM.

I just did many tests recently and tried to run LiveCD on 242MB RAM and I managed to try and install from the LiveCD with this little space of RAM. With other DEs, you can NOT do that.

Let me know if you need any further assistance.

---

### Post by 11jmb on 2011-11-09
> **weese said:**
> I would also like to know if actually installing to an SD card rather than running in the "try it out" mode would would yield resource allocation numbers that are the same as running from a hard drive.

I would guess that it still will use more memory, because you will still be booting from a peripheral device. Report back with results, though.

---

### Post by weese on 2011-11-09
> **amjjawad said:**
> Hello and Welcome to Ubuntu Forum and thanks for choosing Lubuntu :)

Being a Hardware and Software Engineer, will make it easier for us to communicate because I'm sure you will understand what I'm talking about.

[B]Installing Lubuntu on a Hard Disk Drive will give the maximum speed + less memory usage.

[/B]Other than the above statement, speed could be slower and memory usage could be more.

I've been around for two years now. I have downloaded and installed more than 60 Linux Distributions. I do have now many LXDE Distributions installed because I'm doing many tests on daily basis. NOT even once, I've noticed that any LXDE Distribution will use more memory than any other distribution with another DE rather than LXDE, period. Even when trying form LiveCD or LiveUSB, LXDE Distributions didn't require so much RAM.

I just did many tests recently and tried to run LiveCD on 242MB RAM and I managed to try and install from the LiveCD with this little space of RAM. With other DEs, you can NOT do that.

Let me know if you need any further assistance.


I am not really worried about the speed, I was mostly trying to reconcile the memory usage factor. I think 11jmb probably hit the nail on the head by saying that it is probably ram disk usage that is sucking up the extra memory.

---

### Post by amjjawad on 2011-11-09
Lubuntu One Stop Thread - My Signature > Section H (Useful Links)

Please have a look at the first two articles.

---

### Post by amjjawad on 2011-11-09
> **weese said:**
> I am not really worried about the speed, I was mostly trying to reconcile the memory usage factor. I think 11jmb probably hit the nail on the head by saying that it is probably ram disk usage that is sucking up the extra memory.

While you are running Lubuntu without installation, could you please start LXTask (Menu > System Tools > Task Manger) then take a Screenshot and post it here?
When you will press "Print Screen" key, the screenshot will be saved on your Home Folder. Just open PCManFM and you'll find it there. Uploaded it here as attachment.

---

