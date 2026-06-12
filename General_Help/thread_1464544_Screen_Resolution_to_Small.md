---
title: "Screen Resolution to Small"
date: 2010-04-28
forum: General Help
---

### Post by c500 on 2010-04-28
I try again - please help. I cannot even find the right thread!

I would like to learn Ubuntu by doing but fail at the first post. In 2007 I installed on an old Laptop and never got the screen resolution to work. I tried again now (3 years) and same issue. I have a five year old Toshiba laptop and installed 9.10 "successfully". It all works but the screen occupies half the space and the laptop screen is only 12 inches so it is not usable. I played with screen resolutions in system preferences but I am offered choices only up 800 x 600 and that seems to be the problem. I cannot find under Ubuntu driver information for my Toshiba. What I think I need is the ability to get to 1280 x 960 or thereabouts resolution. 

I have no idea how to do this, if I can do this?

I hope it is not another 3 years before I can try Ubuntu again!

---

### Post by LurkyLou on 2010-04-28
Did you check for drivers via System->Administration->Hardware Drivers?

---

### Post by c500 on 2010-04-28
Many thanks

Yes but no luck as it said "no closed or proprietary drivers found". I did find a a way at start up to boot into the original Windows - I had partitioned the drive and I can hopefully find driver details in there. 

After the email, I found the software update app and am installing 257 needed updates! This will take a good 30-40 minutes more. Perhaps, if I am superbly fortunate, one of these updates will allow me to increase my screen resolution - but I am normally not so fortunate.

I found the manual (remember those things) which tells me that I have support for 1024 x 768 XGA


Once the updates are installed, should I try to find all the video driver details on the laptop?

I hope to get over this show stopper as the software looks quite good

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
You should most certainly update but anyway... If you want to know what drivers you need you don't have to reboot. Click the help (yelp) icon and read the manual for lspci (command line program). That will list your hardware. Then do a google search for what drivers you need and how to install them.

Example: ```
Killmandline:$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:07.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation C77 [***nForce 750a SLI***] (rev a2)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
Killmandline:$ 

```
As you can see it's kind of obvious I have an NVIDIA card and with a little research on the nforce 750a I know that the chipset is nvidia 8300 which is supported by the nvidia-current package. So I would type ```
sudo apt-get install nvidia-current
```
Or I can just go into synaptic and search nvidia.

---

### Post by c500 on 2010-04-28
The display adapter is Trident Video Accelerator Cyber - XP4 v6. 4823-104.22_2

---

### Post by CharlesA on 2010-04-28
Try running lscpi and posting the output.

Might help us figure out what chipset that card is using.

---

### Post by dino99 on 2010-04-28
here a small gift only for you:

[http://ubuntuforums.org/showthread.php?p=8441351](http://ubuntuforums.org/showthread.php?p=8441351) page=7 #63

you need to have this package installed: xserver-xorg-video-trident

---

### Post by c500 on 2010-04-28
Thanks for all the help but at the risk of sounding pathetic - I am stuck

I am not a Linux programmer and unfamiliar with Ubuntu so forgive the ignorance.

I type 1spci in help and in terminal and it gives me nothing back - so I cannot find the chipsets

Then I tried dino99's helpful thread but when I am asked to install xserver-xorg-video-trident, I have no idea what that means, where I install it, where I find it

Sorry

---

### Post by dino99 on 2010-04-28
follow my post above #7, and for info it's not 1spci but lspci  ( ie minor L)

---

### Post by QIII on 2010-04-28
Just for future reference, that's lspci -- small "el", not "one"

---

### Post by c500 on 2010-04-28
Ok thanks for the catch on the letter lpsci I will have a go at that

Dino, if I understand the thread 7 to which you point,  I need to incorporate this code somewhere - but I am not sure where

Section "Device"
Identifier "Trident Microsystems CyberBlade XP"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection

---

### Post by c500 on 2010-04-28
Ok thanks for the catch on the letter l I will have a go at that

Dino, if I understand the thread 7 to which you point,  I need to incorporate this code somewhere - but I am not sure where

Section "Device"
Identifier "Trident Microsystems CyberBlade XP"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection

---

### Post by c500 on 2010-04-28
OK found the lspci manual that is the good news

Bad news - means nothing to me and I have no idea what to do

Sorry

---

### Post by dino99 on 2010-04-28
don't panic,

the thread given is about the same graphic card as yours and same distro, so you can compare your xorg.cong ( to open it, into console: sudo gedit /etc/X11/xorg.conf ) and the one posted on that thread , only to show you the differences.

to install xerver-xorg-video-trident, you have to use synaptic: 
menu on top: system --> admin --> synaptic

then search that package and select it to install

---

### Post by c500 on 2010-04-28
OK I got into synaptic package manager and do edit search, type in xerver------ and nothing happens no package is selected remains in the windo

---

### Post by c500 on 2010-04-28
Aha managed to find it the long way and "reinstalled it". Said it was successfully reinstalled.

I rebooted but no joy; nothing has changed

And I did get into termnal sudo.... but the xorg is blank

---

### Post by c500 on 2010-04-29
Any ideas please? Fallen at the first post again. Don't want to wait three years again to try Ubuntu

---

### Post by leizhch on 2010-04-29
> **c500 said:**
> OK I got into synaptic package manager and do edit search, type in xerver------ and nothing happens no package is selected remains in the windo
it would be xserver rather than "xerver"

---

### Post by c500 on 2010-04-29
Thanks - perhaps that was the problem. I did find the package eventually through a long scroll of the list on the bottom right hand side of that screen. But when I did that sudo .... /xorg I did find that I have nothing in my xorg file. So I tried pasting in the long script that is recommended and then saved it - but probably have no idea where to save it - so nothing happens.

I am starting to think that I am not competent enough to use Ubuntu despite the recent claims to the contrary. Pity it looks like a great interface but I cant get out of the starting blocks and am losing heart

I appreciate the help but I seem to stumble at each step

---

### Post by c500 on 2010-04-29
One more idea - I read that 10.4 is out now might that be able to work with my video card or is this not likely to be addressed? And then how can I over write 9.10?

---

### Post by c500 on 2010-05-01
Same issue with 10.4

Worked lpsci and found one line there about the Trident display

01:00.0 VGA campatible controller Trident Cybersytems microblade XP4m32 (rev91) if that helps but I think the script I have been sent relates to that. I have saved it as xserver...... but it does not seem to do the trick. I am offered a few locations to save it however - etc and file system do not seem to work. Root directory???

I have also dug out a 9 year old Dell Laptop and installed 10.4 in it - fills the full screen but no resolution over 860 either. But at least it fills the full screen so I would not want to change it.

---

