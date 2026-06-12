---
title: "media player"
date: 2011-02-07
forum: General Help
---

### Post by piymon on 2011-02-07
what is the best media player to play 1080 p movies without lagging in ubuntu

---

### Post by hariks0 on 2011-02-07
We yell, See !

I mean VLC :P

---

### Post by piymon on 2011-02-07
its lagging in vlc via ubuntu but working fine in vlc via windows 7

---

### Post by piymon on 2011-02-07
> **piymon said:**
> its lagging in vlc via ubuntu but working fine in vlc via windows 7
any other suggestion

---

### Post by Perfect Storm on 2011-02-07
Might be a video card (driver?) issue you have.

Try mplayer - if it also lag, the problem is somewhere else.

---

### Post by piymon on 2011-02-07
yeah its lagging still in fullsize mode but doesnot lag if i reduce the window size.
any other approaches..

---

### Post by Perfect Storm on 2011-02-07
Which video card do you have?

Is the video from a DVD?

Any other applications with similar problems?

---

### Post by piymon on 2011-02-07
even the screen savers are lagging

---

### Post by Perfect Storm on 2011-02-07
Which video card do you have?

---

### Post by piymon on 2011-02-07
where to find the info

---

### Post by Perfect Storm on 2011-02-07
If you want a gui for it, install sysinfo, or use this command to display your card in the terminal;
```
 lspci | grep VGA
```

---

### Post by piymon on 2011-02-07
> **Artificial Intelligence said:**
> If you want a gui for it, install sysinfo, or use this command to display your card in the terminal;
```
 lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation Device 0046 (rev 02)

---

### Post by Perfect Storm on 2011-02-07
Hmmm...that doesn't give much, try;

```
lspci
```

---

### Post by piymon on 2011-02-07
hope this help 
> **Artificial Intelligence said:**
> Hmmm...that doesn't give much, try;

```
lspci
```
> piyush@piyush-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0044 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 0046 (rev 02)
00:16.0 Communication controller: Intel Corporation Ibex Peak HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation Ibex Peak High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Ibex Peak LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Ibex Peak 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Ibex Peak SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation Ibex Peak Thermal Subsystem (rev 05)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Device 2c62 (rev 02)
ff:00.1 Host bridge: Intel Corporation Device 2d01 (rev 02)
ff:02.0 Host bridge: Intel Corporation Device 2d10 (rev 02)
ff:02.1 Host bridge: Intel Corporation Device 2d11 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)
piyush@piyush-laptop:~$ 



---

### Post by oleink on 2011-02-07
Quick question:  What do you have your visual effects set to:

System > Preferences > Appearance > Visual Effects

And how important are things like compiz to you?

---

### Post by piymon on 2011-02-07
> **oleink said:**
> Quick question:  What do you have your visual effects set to:

System > Preferences > Appearance > Visual Effects

And how important are things like compiz to you?

visual effect is none. cant change to any other option

what is compiz

---

### Post by oleink on 2011-02-07
> **piymon said:**
> visual effect is none. cant change to any other option

what is compiz

Compiz is a piece of software for nice visual effects.  Hmmm so you cannot change visual effects?  Intel doesn't usually have the problem you've got.  Could be plugin problem

---

### Post by oleink on 2011-02-07
I've got an idea:  I was thinking to tell you to reinstall something, but do you have restricted extras?  If not, install them

---

### Post by psycho5 on 2011-02-07
try gmplayer. I think the reason your screensaver and videos on fullscreen lag is because your ubuntu partition might be almost full, you might be running low on ram or swap. Or maybe your video card's linux drivers aren't getting the most out of your video card.

---

### Post by uRock on 2011-02-07
Do you have a graphics driver installed? Look in the menu to see, System> Administration> Hardware Drivers.

---

### Post by piymon on 2011-02-08
can u ellaborate on what is restricted extras and what to do with it

---

### Post by piymon on 2011-02-08
> **uRock said:**
> Do you have a graphics driver installed? Look in the menu to see, System> Administration> Hardware Drivers.

attaching the screenshot of what it says

---

### Post by cascade9 on 2011-02-08
@ piymon- the reason why win7 plays 1080p without problems and ubuntu isnt will (probably) be because with winodws the intel video is using at least some hardware video decoding. 

With linux, you normally need to setup those sorts of things yourself. VA-API is what you should look into. 

> **uRock said:**
> Do you have a graphics driver installed? Look in the menu to see, System> Administration> Hardware Drivers.

For intel? LOL. Theres no proprietary intel video drivers AFAIK, and thats all jockey is good for, getting proprietary drivers.

---

### Post by piymon on 2011-02-08
> **cascade9 said:**
> @ piymon- the reason why win7 plays 1080p without problems and ubuntu isnt will (probably) be because with winodws the intel video is using at least some hardware video decoding. 

With linux, you normally need to setup those sorts of things yourself. VA-API is what you should look into. 



For intel? LOL. Theres no proprietary intel video drivers AFAIK, and thats all jockey is good for, getting proprietary drivers.

now what is VA-API

---

### Post by cascade9 on 2011-02-08
[http://en.wikipedia.org/wiki/Video_Acceleration_API](http://en.wikipedia.org/wiki/Video_Acceleration_API)

---

### Post by piymon on 2011-02-08
thanks for help guys..
i have installed ubuntu 10.10 and 1080p is no longer a issue.thanks for ur help

---

