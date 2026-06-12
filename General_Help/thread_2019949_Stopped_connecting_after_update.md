---
title: "Stopped connecting after update"
date: 2012-07-07
forum: General Help
---

### Post by needastick on 2012-07-07
My system will not connect to the net automatically when I boot up. This stopped happening following a recent update. The network connection on the toolbar shows an exclamation mark and reads 'no connection'

This is a dual boot and the other o/s connects OK. If I right click and disable internet connection on the Ubuntu and then re-enable a couple of times, I hear the HD whir a bit and it establishes the connection and maintains it until I close down.

I now want to do a fresh install of 12.04 and I am worried that it will not be able to download the necessary repositories etc whilst booting from the live disc. I feel I need to repair this first.

I've been through the usual network screens but they're beyond my knowledge, can anyone help me please?

---

### Post by lrcaballero on 2012-07-07
Are you able to connect and/or see any networks when you right click on your network icon? If you are what happens when you attempt to connect?

Also if you want to do a clean install of 12.04 check that you are able to connect to your network while running the live cd.....

---

### Post by needastick on 2012-07-07
Hello,
         no, the connection information option is greyed out. It becomes available only afterwards.
I was unable to connect when I tried the live cd, I don't know why this is as you usually don't have an os at all when you're installing.

---

### Post by lrcaballero on 2012-07-07
While running on Live CD, try right clicking and select change background desktop, then click on All Settings tab, under Hardware do you see any additional drivers available for your network?

---

### Post by Bucky Ball on 2012-07-07
> **lrcaballero said:**
> 

Also if you want to do a clean install of 12.04 check that you are able to connect to your network while running the live cd.....

This won't prove much as, even if your card is going to work on a hard drive install, it will not work booting from the LiveCD if it needs third-party drivers, as many do. You can not install drivers (wireless or graphics and others) or apps to a Live boot as there's nowhere to install them to. You are running from a closed CD/DVD/USB media; it's not writable.

---

### Post by lrcaballero on 2012-07-07
Bucky Ball: would this help him to at least determine if the drivers will be available (if applicable) after install? Please advise...

Thank you,

---

### Post by Bucky Ball on 2012-07-07
As a matter of fact, yea, you're right. It just might ...

---

### Post by needastick on 2012-07-07
Tried the right click whilst on live cd but no dice. It's showing 'cable unplugged' when I query network and no results on the driver tag.

---

### Post by Bucky Ball on 2012-07-07
Out of curiousity; how did you get connected when you first installed Ubuntu? Did you need to do anything to get your internet happening? If so, what? You may just need to repeat the procedure, if you remember what that was.

Could you paste this into a terminal and post the output:

sudo lshw -C network

---

### Post by needastick on 2012-07-07
I can't remember that, it was about three years ago. I am able to get online but I'm having to fiddle about instead of it working automatically. I'm posting this from windows 7 at the mo, working fine over here.

---

### Post by Bucky Ball on 2012-07-07
What are you doing to get it online? What fiddling?

---

### Post by needastick on 2012-07-07
I have to right click on the network icon then disable it. I then try a website which brings the unable to locate server window, then when I re-enable the network tab it connects.

This has only developed recently but I don't know whether it is as a result of an ubuntu update or a bios flash. The connection works happily in windows so I think it must be a linux issue.

I have tried reinstalling the network manager and applets but that hasn't worked. Any ideas?

---

### Post by needastick on 2012-07-07
Bucky ball
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:26:18:fe:6d:54
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.2 latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febf0000-febfffff(prefetchable)

sorry I missed where you asked for this.

---

### Post by needastick on 2012-07-07
I've marked this thread as solved but unfortunately I'm not sure how I did it. I have reinstalled the gnome manager in synaptic again and repeatedly booted and it now appears to be playing good.

I'll install 12.04 while the going's good.

Thanks for your help guys.O:)

---

### Post by Bucky Ball on 2012-07-07
Good news and good luck with it all. ;)

---

