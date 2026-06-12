---
title: "what's the difference between installing lxde or lubuntu?"
date: 2011-10-23
forum: General Help
---

### Post by lianazaman on 2011-10-23
I see two choices:

sudo apt-get install lxde

and sudo apt-get install lubuntu-desktop.

Aren't those two the same thing, or are they different? In...? one is desktop, one is...?installation size?

---

### Post by mike555 on 2011-10-23
if you want to try lxde on ubuntu ,you should get "lxde-core " it won't install so much stuff , otherwise lxde will install a bunch of Lubuntu stuff .
   if you really want lxde you should try the Lubuntu cd..... you might not like it because it is very light on apps.
   I use Xubuntu, it seams like a good compromise between lightness with good apps.

---

### Post by amjjawad on 2011-10-23
> **lianazaman said:**
> I see two choices:

sudo apt-get install lxde

and sudo apt-get install lubuntu-desktop.

Aren't those two the same thing, or are they different? In...? one is desktop, one is...?installation size?

Hi,

I'd suggest to check my thread (Lubuntu One Stop Thread) and you'll find many useful information.

[Lubuntu]("https://wiki.ubuntu.com/Lubuntu") is an Operating System that is using [LXDE]("http://lxde.org/").

---

### Post by lianazaman on 2011-10-24
> **mike555 said:**
> if you want to try lxde on ubuntu ,you should get "lxde-core " it won't install so much stuff , otherwise lxde will install a bunch of Lubuntu stuff .
   if you really want lxde you should try the Lubuntu cd..... you might not like it because it is very light on apps.
   I use Xubuntu, it seams like a good compromise between lightness with good apps.

Woah, thanks for the info! I was intending to try lxde on ubuntu, sans the multiple apps. I notice some of the apps, while different names, held same uses, which kind of confuses me. So in short, I want to desktop environment but still using the same apps for both environment. Wait, is that even possible?   


> **amjjawad said:**
> Hi,

I'd suggest to check my thread (Lubuntu One Stop Thread) and you'll find many useful information.

[Lubuntu]("https://wiki.ubuntu.com/Lubuntu") is an Operating System that is using [LXDE]("http://lxde.org/").

Lubuntu means the whole distro right? Okay, cool... right now I only want to try the DE or 'shell', but who knows, with the addition of many advanced apps, and my laptop ain't going to be any more advanced, this could be the best choice out of all ubuntu distros when it come to performance. :) Monitoring set!

---

### Post by amjjawad on 2011-10-24
> **lianazaman said:**
> I want to desktop environment but still using the same apps for both environment. Wait, is that even possible?   
YES in most cases. Sometimes, you need a work-around to get it to work. Compiz for example works on LXDE but not of of the box, you need to configure it little bit.

> Lubuntu means the whole distro right?
Right :) 

> right now I only want to try the DE or 'shell', but who knows, with the addition of many advanced apps, and my laptop ain't going to be any more advanced, this could be the best choice out of all ubuntu distros when it come to performance

Download Lubuntu (11.10 is the latest version), use UNetbootin to create Live-USB and give it a try. Even Live-CD will do the job.
I'm sure you'll love it and install it :)

If you need anything related to Lubuntu, please let me know.
On my signature, there is a link for almost everything you need to know about Lubuntu :)

---

### Post by lianazaman on 2011-10-24
> **amjjawad said:**
> YES in most cases. Sometimes, you need a work-around to get it to work. Compiz for example works on LXDE but not of of the box, you need to configure it little bit.


Right :) 



Download Lubuntu (11.10 is the latest version), use UNetbootin to create Live-USB and give it a try. Even Live-CD will do the job.
I'm sure you'll love it and install it :)

If you need anything related to Lubuntu, please let me know.
On my signature, there is a link for almost everything you need to know about Lubuntu :)

You know what? While I'm not  deleting the Unity , I am interest in installing the lubuntu desktop, because:
1. Good reviews of the performance, even on very,very old hardwares
2. My Unity, even on Unity 2D, is a bit sluggish (this is 2 years old already, age catches up I guess in tech world)
3. You profile pic of Monkey D. Luffy is one of my fav char! (biased, but who cares?)

---

### Post by amjjawad on 2011-10-24
> **lianazaman said:**
> You know what? While I'm not  deleting the Unity , I am interest in installing the lubuntu desktop, because:
1. Good reviews of the performance, even on very,very old hardwares
2. My Unity, even on Unity 2D, is a bit sluggish (this is 2 years old already, age catches up I guess in tech world)
3. You profile pic of Monkey D. Luffy is one of my fav char! (biased, but who cares?)

Well, I do have another opinion about that. I'm one of those who like to try/use everything on its native environment. Installing Lubuntu 11.10 for example is NOT exactly the same as installing "lubuntu-desktop" package even if it looks the same. However, this is my personal opinion. I hold the same opinion even for Wine and Wubi because I don't like them both and never used them.

Your core system is Ubuntu and you'll add just another DE and the performance IMHO won't be the same. After all, your call.

Thanks. Luffy is one of my favorite characters even though I'm 30 years old but I enjoy when I watch these stuff. I have many other favorite characters too.

---

### Post by lianazaman on 2011-10-25
to amjjawad:

1. Need help. trying the Lubuntu Live CD, but could not activate broadband driver. According to my experience with Ubuntu, I need to activate the driver before installing, if not it would just say (firmware missing). Which is weird, considering Ubuntu can detect and activate my driver, but Lubuntu couldn't. 

Is there something wrong I should take notice about, or is there any other alternative to activate the driver?

it said check the jockey.log, but since it's from the live CD, where should I find it?

---

### Post by amjjawad on 2011-10-25
> **lianazaman said:**
> to amjjawad:

1. Need help. trying the Lubuntu Live CD, but could not activate broadband driver. According to my experience with Ubuntu, I need to activate the driver before installing, if not it would just say (firmware missing). Which is weird, considering Ubuntu can detect and activate my driver, but Lubuntu couldn't. 

Is there something wrong I should take notice about, or is there any other alternative to activate the driver?

it said check the jockey.log, but since it's from the live CD, where should I find it?

As far as I know, you can do that after installation.
What is your Network Card? 
```
sudo lshw -C network
```

The point of trying any distribution from the Live-CD or Live-USB is to check whether your hardware drivers will work out of the box or not? beside some other advantages.
If it worked with another release it doesn't mean it will work too on the new one. Kernels are different from one release to another.

---

### Post by lianazaman on 2011-10-25
Ah, now I know....bummer, I was thinking of making this a lubuntu-windows dualboot instead of ubuntu(with lxde)-windows. After I installed it, I couldn't update or anything because it says firmware missing. And when I tried additional drivers, if during the live CD it has the Broadband SATA Driver (if I'm not mistaken), no it saya downloading packages failed.




```
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:91100000-91103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:bf:52:c6
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:2000(size=256) memory:91010000-91010fff memory:91000000-9100ffff memory:91020000-9103ffff
  *-network** [COLOR=Black]DISABLED[/COLOR]**
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:82:11:44:2a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware**=N/A **link=no multicast=yes wireless=IEEE 802.11bg

```


Erm...if you know multiple solutions, can you post it all? Because I think it would be 'exhausting' for my laptop to keep rebooting so I can check the troubleshooting at windows for the lubuntu. ^_^;

---

### Post by lianazaman on 2011-10-25
Solved. I plugged in my sis' mobile broadband, go to synaptic and install the bcmwl-kernel-source. Restart, and it's detectable and activated :).

Not bad for a once computer-illiterate girl huh? ^o^

---

### Post by kurt18947 on 2011-10-25
> **lianazaman said:**
> Solved. I plugged in my sis' mobile broadband, go to synaptic and install the bcmwl-kernel-source. Restart, and it's detectable and activated :).

Not bad for a once computer-illiterate girl huh? ^o^

Nicely done.  That chipset seems to be one of the bigger problem children of Linux WiFi family.

---

### Post by amjjawad on 2011-10-25
> **lianazaman said:**
> Solved. I plugged in my sis' mobile broadband, go to synaptic and install the bcmwl-kernel-source. Restart, and it's detectable and activated :).

Not bad for a once computer-illiterate girl huh? ^o^

I'm glad you managed to fix it and sorry for my late reply, I'm doing 10 things at the same time with many opened tabs.

Please, if you have any other issue regarding Lubuntu, let me know.
If you have to start a new thread for a new problem, PM me the link :)

---

