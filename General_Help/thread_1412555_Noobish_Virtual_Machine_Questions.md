---
title: "Noobish Virtual Machine Questions"
date: 2010-02-21
forum: General Help
---

### Post by boombox1387 on 2010-02-21
So, I've never messed around much with VMs, but I need to do some reinstalling sometime soon, and I thought I might give it a shot.  

Recently I've only been using Windows occasionally to play games that don't run in Wine.  It hardly deserves it's own partition at this point, but before I install it in a Virtual Machine, I have some questions:

-Most importantly, does this mean I'll need to reinstall Windows every time I reinstall Ubuntu?  I do a fresh Ubuntu install once a year, but installing Windows is a long and painful process that I try to avoid as much as possible.  Is it possible to backup a virtual installation of Windows so I don't have to reinstall it every year?

-VMWare or Virtualbox?  I don't want to start any flamewars, and I doubt I'll be very picky.  My needs are fairly simple, but if one of those two pieces of software has emerged as clearly dominant, that would be good to know.

Thanks in advance.

---

### Post by gmargo on 2010-02-21
I can't speak for VirtualBox, but under Vmware, each virtual machine resides in it's own directory.  Back up those directories/files just like you back up everything else.  Personally, I store my virtual machines in a directory under /home which is on a different partition from the root partition.

---

### Post by boombox1387 on 2010-02-21
> **gmargo said:**
> I can't speak for VirtualBox, but under Vmware, each virtual machine resides in it's own directory.  Back up those directories/files just like you back up everything else.  Personally, I store my virtual machines in a directory under /home which is on a different partition from the root partition.

Thanks for the quick response; this is exactly what I had been hoping for.  It would make sense that Virtualbox would do things similarly, but if someone knows for sure, I'd be glad to hear your input.  Otherwise I might test it out myself.

---

### Post by mkvnmtr on 2010-02-21
In virtual box the guest systems reside in their on file that can be backed up or even copied and tranfered to another machine. Once you set one up you can also put it on another machine or give it to a friend to run on his machine. I believe there are sites on the internet where you can download the machine and import it into your system.

---

### Post by boombox1387 on 2010-02-21
> **mkvnmtr said:**
> In virtual box the guest systems reside in their on file that can be backed up or even copied and tranfered to another machine. Once you set one up you can also put it on another machine or give it to a friend to run on his machine. I believe there are sites on the internet where you can download the machine and import it into your system.

Very cool.  I'm looking forward to messing around with this a bit over the next few days.

---

### Post by bodhi.zazen on 2010-02-21
VirtualBox will be easier to install as VMWare does not support Ubuntu.

Also, Virtualization does NOT use you hardware directly and you may not have much luck playing games, you will have to try and see.

Install the VB guest additions or VMWare toolbox.

---

### Post by boombox1387 on 2010-02-22
> **bodhi.zazen said:**
> 
Also, Virtualization does NOT use you hardware directly and you may not have much luck playing games, you will have to try and see.

Good to know.  I'm not a heavy gamer, and most of my games are more than a few years old, but without hardware acceleration... who knows.

I'm not as rushed to reinstall as I originally thought, so I'll test Virtualbox out a bit before I wipe away my Windows partition.  It would be perfect if all I needed it for was testing website in IE... stupid games... =)

---

### Post by Ozymandias_117 on 2010-02-22
> **bodhi.zazen said:**
> VirtualBox will be easier to install as VMWare does not support Ubuntu.

Um... VMware DOES have a linux version - Which works perfectly on my ubuntu 9.10 machine.

---

### Post by bodhi.zazen on 2010-02-22
> **Ozymandias_117 said:**
> Um... VMware DOES have a linux version - Which works perfectly on my ubuntu 9.10 machine.

Glad it works for you. I have switched to KVM / Openvz, and LXC, all of which are open source and fit my needs. Much less hassle then VMWare and tweaking the installer (certainly the VMWare installer has not always been so easy).

With Ubuntu 10.04 I have to re-do the Virtualization mega thread, so I will certainly update the thread for VMWare as well.

---

### Post by howefield on 2010-02-22
> **boombox1387 said:**
> Is it possible to backup a virtual installation of Windows so I don't have to reinstall it every year?

You can install your guest where ever you want, even on a separate partition on preferably a separate disk for best performance. This makes backing up or reinstalling as in your case very easy. Virtualbox also has an export function that you can use to back up your vms.

> -VMWare or Virtualbox?

I'd recommend Virtualbox PUEL (Personal Use & Evaluation License) from virtualbox.org over the OSE (Open Source Edition) that you'll find in the repository (if you want to use USB devices in your guest).

---

