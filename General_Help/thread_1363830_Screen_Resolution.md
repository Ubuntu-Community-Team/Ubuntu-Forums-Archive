---
title: "Screen Resolution?"
date: 2009-12-24
forum: General Help
---

### Post by Roasted on 2009-12-24
What's up with Kubuntu and screen resolution? I have Karmic installed on a new computer here with a 22 inch screen. This 22 inch LCD is kind of dull and 1680x1050 resolution on it (native) renders text very poorly. I set it to 1024x768 and applied. I rebooted shortly after. It came up as 1680x1050 again. So I went to system settings to change the resolution again. The second I hit "display" my monitor went black, and up came the 1024x768 resolution. It's like it was like OH HEY JUST KIDDING NOW I REMEMBER WHAT YOU SET ME TO BEFORE.

I mean, come on. It's just a screen resolution. Why is it giving me a headache? It's like it wants the native resolution and that's IT. Any idea?

---

### Post by lidex on 2009-12-25
Can you post the output of these commands?
```
sudo lshw -C video
lspci
```

---

### Post by lidex on 2009-12-25
Ooops

---

### Post by Roasted on 2009-12-25
> **lidex said:**
> Can you post the ouyput of these commands?
```
sudo lshw -C video
lspci
```

At the moment I can't. The computer I noticed this with is wrapped up under the tree. I'll get back to this post when I can in regard to the commands you asked me to run. :popcorn:

---

### Post by lidex on 2009-12-25
> At the moment I can't. The computer I noticed this with is wrapped up under the tree. I'll get back to this post when I can in regard to the commands you asked me to run.
HaHa. Merry Xmas.

---

### Post by Roasted on 2009-12-25
```
curt@curt-nix-desktop:~$ sudo lshw -C video
[sudo] password for curt:                  
  *-display                                
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]        
       vendor: nVidia Corporation            
       physical id: 0                        
       bus info: pci@0000:01:00.0            
       version: a1                           
       width: 64 bits                        
       clock: 33MHz                          
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0                 
       resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:d800(size=128) memory:fea80000-feafffff(prefetchable)
curt@curt-nix-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
curt@curt-nix-desktop:~$

```

---

### Post by Roasted on 2009-12-25
I just tested the same thing on my Kubuntu work laptop. I set the resolution to 800x600 and hit apply and rebooted. It came back as the native resolution, which is like 1280x800. Once I went to system settings and hit "display" BLAM 800x600 came back. Grr...

So someone suggested, just fire up nvidia-settings and make the changes. Well, for the desktops this might be true since they have nvidia cards. But my work laptop has an intel graphics card. What is the "nvidia-settings" equivalent of intel?

What do I need to do? I never thought screen resolution would be such a headache.

Is this something KDE dependent? Or is this a problem with the xorg.conf itself?

EDIT - It seems as if it's KDE. I just fired up Fedora 12 - KDE on my spare computer. Did the exact same thing.

EDIT 2 -  It seems as if it's not totally KDE. In Fedora 12, there's an option under "administration" (something Kubuntu appears to not have) to launch system-config-display as root. When you do that, it saves the settings accordingly to xorg. Therefore, it works in Fedora 12, as long as you change it under administration. In Kubuntu, it doesn't seem possible. Oddly enough, if you click on system settings - display, it'll auto-change the session to whatever those settings are. AKA - if you have your xorg set to 1680x1050, but display settings are 1024x768, the second you click on "display" it'll shoot the resolution to that. So I guess a good word of advice is, if you're on Fedora and you want the resolution changed to something different, install system-config-display, kickoff menu - applications - administration - display, change to your desired resolution, then change system settings - display to the same. Blam. Works then in Fedora (due to system-config-display writing the changes to xorg). Not sure why KDE in *buntu doesn't have this option, but meh. Life goes on I guess.

---

### Post by lidex on 2009-12-26
Try this:
[http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html]("http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html")

---

### Post by BrettD on 2009-12-26
Try running KRandRTray ("K -> System > KRandRTray").  This application sits in the system tray and duplicates the functionality (including remembering the settings that you are using) of the display settings in the system setting.

---

### Post by cascade9 on 2009-12-26
If you've got nVidia drivers installed, then go to terminal-

sudo nividia-settings

Change the resolution there and the settings should 'stick'.

---

### Post by Roasted on 2009-12-26
> **cascade9 said:**
> If you've got nVidia drivers installed, then go to terminal-

sudo nividia-settings

Change the resolution there and the settings should 'stick'.

What about for intel users, such as myself?

See my frustration now?

---

### Post by Roasted on 2009-12-26
> **BrettD said:**
> Try running KRandRTray ("K -> System > KRandRTray").  This application sits in the system tray and duplicates the functionality (including remembering the settings that you are using) of the display settings in the system setting.

Upon rebooting the settings did not stick.

---

### Post by Chame_Wizard on 2009-12-26
try 

```
sudo xrandr -s 1024x768
```

---

### Post by BrettD on 2009-12-26
> **Roasted said:**
> Upon rebooting the settings did not stick.

Odd.  Under normal conditions if KRandRTray was running when you shut down the machine, I would expect it to start again when you next login (unless you have KDE configured to not restore the previous session on login).  

You might also find this page: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) contains some useful ideas.

---

### Post by lidex on 2009-12-26
> **Roasted said:**
> What about for intel users, such as myself?

See my frustration now?

OK, now I'm confused.


> description: VGA compatible controller
       product: G96 [GeForce 9400 GT]        
       vendor: nVidia Corporation            


---

### Post by Roasted on 2009-12-27
> **lidex said:**
> OK, now I'm confused.

The 9400 GT was from the one desktop. The Intel is what my laptop uses, which I'm having this issue with. Sorry I got mixed up.

---

### Post by chewearn on 2009-12-27
Actually intel is doing it right by using standard xorg utility.  My guess is Ubuntu got a bug.  Perhaps a search in Launchpad will turn something up, or else please file bug.

nvidia-settings, while full of features, is a separate utility that tried to work around xorg.  Most times, it succeed beautifully, but sometimes the breakage can be full of pain.  I have to fiddle with nvidia-settings every six months when a new Ubuntu version came out.

---

### Post by lidex on 2009-12-27
Can you humor me and post the output of these commands on your laptop?
```
sudo lshw -C video
lspci
```

---

### Post by Roasted on 2009-12-27
> **lidex said:**
> Can you humor me and post the output of these commands on your laptop?
```
sudo lshw -C video
lspci
```

 
```
jason@FOG-Laptop:~$ sudo lshw -C video
[sudo] password for jason:            
  *-display:0                         
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation                                      
       physical id: 2                                                 
       bus info: pci@0000:00:02.0                                     
       version: 07                                                    
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:f6c00000-f6ffffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6b00000-f6bfffff



jason@FOG-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
02:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)


```

---

### Post by lidex on 2009-12-27
Go here:
[http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html]("http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html")
and follow instructions, inserting "karmic" for "jaunty" where needed.

---

### Post by Roasted on 2009-12-27
> **lidex said:**
> Go here:
[http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html]("http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html")
and follow instructions, inserting "karmic" for "jaunty" where needed.

Just curious, how would newer drivers work around what I'm seeing with KDE? I'm in Fedora KDE as we speak and it's doing the same thing here, evident it's a KDE issue where the resolution you select won't stick upon rebooting.

But even still, I look at KDE as the desktop environment I'd give my mom if I put *buntu on her pc. And if you can't do something simple like change the resolution, that just shaves off some points off the top, since I know she uses a certain resolution on her pc. *shrug*

---

### Post by Roasted on 2009-12-29
I still have to question the obvious.

How does this work on Ubuntu without editing the xorg file, yet it doesn't work on Kubuntu without editing the xorg file? I tested KRandR more and while I see how it can be useable as a solution for my situation, I still have to ask how Ubuntu can do it while Kubuntu can't. What's different here?

---

### Post by audiomick on 2009-12-29
> **Roasted said:**
> I still have to question the obvious.

How does this work on Ubuntu without editing the xorg file, yet it doesn't work on Kubuntu without editing the xorg file? I tested KRandR more and while I see how it can be useable as a solution for my situation, I still have to ask how Ubuntu can do it while Kubuntu can't. What's different here?

The desktop. I can't go into any detail, it's way over my head, but that is the difference, I reckon. The desktop "communicates" with the x-server, and they both do it a bit different to each other, which provides a possible explanation why one looks at xorg.conf and the other doesn't.

The fact that Gnome isn't looking at xorg.conf is an indication that Gnome is perhaps "more up to date".

---

### Post by Roasted on 2009-12-29
> **audiomick said:**
> The desktop. I can't go into any detail, it's way over my head, but that is the difference, I reckon. The desktop "communicates" with the x-server, and they both do it a bit different to each other, which provides a possible explanation why one looks at xorg.conf and the other doesn't.

The fact that Gnome isn't looking at xorg.conf is an indication that Gnome is perhaps "more up to date".

Yet Gnome has been in 2.x for 7 years while KDE has continually came out with updates and newer editions. Not to get into a desktop environment war here seeing as though I like both a lot for different reasons, but to indicate Gnome is more up to date based on that alone isn't really accurate... in my opinion, at least.

Even still, it seems as if KDE does indeed apply the resolution at the "desktop level" in the same manner Gnome does, now that I play around with it more. However, the way to achieve that is to enable KRandR tray. Then when you reboot, since KDE restores sessions, it also fires up KRandR tray and changes your resolution immediately upon boot. I guess if you confingured KDE to not restore sessions, you could still tack KRandR tray into the startup applications to get it rolling that way.

Even though this all makes sense in how they work, I just still had to question it. To "lock" it in place with KDE with KRandR tray you just have to log out or reboot with KRandR tray still enabled, I suppose.

---

### Post by lidex on 2009-12-29
May be late, but informative:
[http://kubuntuforums.net/forums/index.php?topic=3108283.0]("http://kubuntuforums.net/forums/index.php?topic=3108283.0")

---

### Post by Roasted on 2009-12-29
So for future reference, say xorg bombs out and I need to reset it.

I boot up, grub comes up. I select Kubuntu. Then what? Hit "E" and that brings up safe mode? What command would I issue at that point? Is there any sort of official documentation for this? I find it interesting and informative yet I've never heard of it before.

---

