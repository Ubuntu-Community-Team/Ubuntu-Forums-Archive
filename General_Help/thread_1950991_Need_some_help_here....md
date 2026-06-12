---
title: "Need some help here..."
date: 2012-04-01
forum: General Help
---

### Post by meduser on 2012-04-01
Hi,

I have been using Kubuntu since I started with Linux a few months ago. Now I am starting to move away from KDE as I have been told by one of my instructors that it is a dead platform, and I should move over to regular Ubuntu.


I love the KDE environment, and the easy layout of the page. On Ubuntu, I am having issues with the desktop. I have dual monitors. I have gone into display, and have them both showing the desktop. I can move my mouse from one desktop to the other, seamlessly with ease. However, I can move anything from the main monitor. If I try to move Chromium from one display to the other, it won't let me. If I try to move say the terminal, it won't let me. I would also like to change the theme, but every time I go to make the new folder themes, the system is freezing, and a hard restart is the only way I have been able to get going again. This has just started happening since I have started trying Ubuntu. Kubuntu does not have that problem. 

I would also like to be able to change the wall paper and have two different wallpapers, one on each monitor, and so far all I have been able to do is change the wallpaper, but it changes both screens, not just one side.

Any help is greatly appreciated. 

I have 4gbs of ram, over 100gbs free space on hdd, and my video card is an nvidea 210. 

I think the video card might be the issue here, as Kubuntu sees it for what it is, but the video in Ubuntu has the drivers listed as something else.

On a side note, my pc also has started taking like 5 minutes from boot to loaded....I don't know why the slowdown, but it gets to the point of thinking it is frozen, then it just starts the login screen...


Any help is greatly appreciated. Thanks

Med

---

### Post by idoitprone on 2012-04-01
> **meduser said:**
> Hi,

I have been using Kubuntu since I started with Linux a few months ago. Now I am starting to move away from KDE as I have been told by one of my instructors that it is a dead platform, and I should move over to regular Ubuntu.


I love the KDE environment, and the easy layout of the page. On Ubuntu, I am having issues with the desktop. I have dual monitors. I have gone into display, and have them both showing the desktop. I can move my mouse from one desktop to the other, seamlessly with ease. However, I can move anything from the main monitor. If I try to move Chromium from one display to the other, it won't let me. If I try to move say the terminal, it won't let me. I would also like to change the theme, but every time I go to make the new folder themes, the system is freezing, and a hard restart is the only way I have been able to get going again. This has just started happening since I have started trying Ubuntu. Kubuntu does not have that problem. 

I would also like to be able to change the wall paper and have two different wallpapers, one on each monitor, and so far all I have been able to do is change the wallpaper, but it changes both screens, not just one side.

Any help is greatly appreciated. 

I have 4gbs of ram, over 100gbs free space on hdd, and my video card is an nvidea 210. 

I think the video card might be the issue here, as Kubuntu sees it for what it is, but the video in Ubuntu has the drivers listed as something else.

On a side note, my pc also has started taking like 5 minutes from boot to loaded....I don't know why the slowdown, but it gets to the point of thinking it is frozen, then it just starts the login screen...


Any help is greatly appreciated. Thanks

Med


ouch kde on ubuntu
sighhh

if you want to use kde, i recommend opensuse or arch. Ubuntu do not devote enough resources to make kde stable enough. Last I heard, they already reassign their only full-time kubuntu employee.

---

### Post by meduser on 2012-04-01
Yeah, I am moving away from KDE to just straight up Ubuntu, but need to get the desktop figured out so that it works for me the way I need it to.

---

### Post by grahammechanical on 2012-04-01
Are you dual booting between Kubuntu and Ubuntu? Or have tried to remove the Kubuntu desktop and replace it with the Ubuntu desktop?

When the OS takes its time to load I think that it is because it is trying to sort out conflicts in the configuration files. Or having to make repeated attempts to make connections.

How can KDE be a dead platform when companies are releasing tablet PC with KDE on it?

[http://www.omgubuntu.co.uk/2012/02/e200-kde-tablet-to-ship-may-pre-orders-open-next-week/]("http://www.omgubuntu.co.uk/2012/02/e200-kde-tablet-to-ship-may-pre-orders-open-next-week/")

Kubuntu is an independent derivative of Ubuntu as is Xubuntu, Lubuntu, Ubuntu Studio, Edubuntu. They are part of the official Ubuntu family but they are not the responsibility of Canonical to develop. They are not different OS departments of Ubuntu.

You have run Kubuntu. So, you tell us, Was it stable?

Kubuntu will continue to be developed. KDE is not a dead platform so why should anyone say that Kubuntu is not going to be developed any more.

This link says the Kubuntu 12.04 will be supported for 5 years.

[http://www.kubuntu.org/]("http://www.kubuntu.org/")

Just last weekend I was install testing the 12.04 Beta 2 ISO images. I intend to share in testing ISO images of all the Ubuntu family during the next development cycle.

Regards.

---

### Post by meduser on 2012-04-01
Kubuntu was nice for the most part, but I like the layout of Ubuntu's menu's and It just seems more polished.


It is stable enough...I just went into my options at login, and changed it from KDE to Gnome..

---

### Post by oldos2er on 2012-04-01
> **meduser said:**
> I have been using Kubuntu since I started with Linux a few months ago. Now I am starting to move away from KDE as I have been told by one of my instructors that it is a dead platform, and I should move over to regular Ubuntu.
Med

KDE is alive and kickin', I assure you, and Kubuntu is not dead either: [http://www.nixternal.com/kubuntu-is-not-dead/](http://www.nixternal.com/kubuntu-is-not-dead/)

---

### Post by meduser on 2012-04-01
OK, Kubuntu isn't going to die. That is a great thing.

 On Ubuntu, I am having issues with the desktop. I have dual monitors. I have gone into display, and have them both showing the desktop. I can move my mouse from one desktop to the other, seamlessly with ease. However, I can move anything from the main monitor. If I try to move Chromium from one display to the other, it won't let me. If I try to move say the terminal, it won't let me. I would also like to change the theme, but every time I go to make the new folder themes, the system is freezing up.

Any ideas or know of any how to's for setting up the desktop as custom?

---

### Post by imachavel on 2012-04-01
drivers are recognized as something else?

yes I wouldn't say kde is a dead platform, but not a lightweight one, definitely not an interface that would be used on a recovery cd like gparted. Now do me a favor, open the terminal with ctrl+alt+t and type this in:

lspci

and post output syntax please. You could try looking for the newest drivers from your gpu manufacturer website, and see if there is a linux version, otherwise try I suppose the windows 7 drivers over the xp drivers, and see if you can install them as restricted drivers, it might not work unless you go to system settings > restricted drivers and try and install them from there. Not guaranteed to work either.

Other then that, no advice, try this from terminal

sudo apt-get upgrade
sudo apt-get update
sudo apt-get upgrade

I know it's repetitive, I don't know see if installing them in different order shows that an upgrade needed to be installed before an update, or maybe that an update needed to be installed before an upgrade

---

### Post by meduser on 2012-04-02
LSPCI:

```

home:~/Desktop$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by meduser on 2012-04-03
So, 

everyone coming to this post seems to be focused on whether or not Kubuntu(KDE) is alive and well. 


The bigger issue here is my issues here with Ubuntu.

Can someone help?

Please?

---

### Post by bobman321123 on 2012-04-03
> **meduser said:**
> So, 

everyone coming to this post seems to be focused on whether or not Kubuntu(KDE) is alive and well. 


The bigger issue here is my issues here with Ubuntu.

Can someone help?

Please?

This isn't a perfect solution, but as far as I know, the development version of Ubuntu (set to be released this month), 12.04 has put major development into dual monitors. 
I'm using it right now, it has a few hickups, but it's moreorless stable overall.

---

### Post by squilookle on 2012-04-03
I ranted about using the DE that works best for you and then decided it wasn't helpful. Hence the edit. 

When I change DE, I always prefer to do a clean install, even though I know you shouldn't have to. I'm also of the impression that support for multiple monitors in Unity isn't ideal (although I never tried it) and I wonder if 12.04 might fix some of the issues. Have you tried running 12.04 from a live CD to see how the monitors behave? If you have issues with graphics drivers not working properly from live CDs, then this may not help either. 

Good luck.

---

### Post by meduser on 2012-04-03
> **bobman321123 said:**
> This isn't a perfect solution, but as far as I know, the development version of Ubuntu (set to be released this month), 12.04 has put major development into dual monitors. 
I'm using it right now, it has a few hickups, but it's moreorless stable overall.

Yeah..can't wait for the LTR....should be fun.

---

### Post by bobman321123 on 2012-04-04
It's looking pretty fantastic, actually.
I'm using gnome-shell on it, but whichever DE you use, it's looking to be awesome.

---

