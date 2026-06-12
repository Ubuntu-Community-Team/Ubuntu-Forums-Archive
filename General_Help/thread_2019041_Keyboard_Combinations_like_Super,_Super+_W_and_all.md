---
title: "Keyboard Combinations like Super, Super+ W and all others are not working"
date: 2012-07-06
forum: General Help
---

### Post by UNME on 2012-07-06
Hi,

Using Ubuntu after long time and wow it has changed a lot.
[COLOR="Navy"]
I had some weird issue:
In Live CD - All the keyboard combinations that are default in Unity like Super + w, Super (long press) were working and even the application stack in Left Panel was folding in 3d fashion if applications were more than screen size.[/COLOR]

After installing it on Hard disk none of the above seems to be working.

1) I checked if there are any addition drivers required: Clicked Additional drivers and it said - No Additional driver installed

2) I am running in Unity mode not Unity 2-d mode.

3) Compiz is running and I have not installed any composting software or setting manager for Compiz / Compiz fusion.

4) Checking Details - Graphics - 
Drive Unknown 
Experience Standard

So everything is right of the box but still Combinations that were working in Live CD are not working now.

I am running Ubuntu 12.04
Any help would be great.

Thank you
UNME

---

### Post by UNME on 2012-07-07
I ran echo $DESKTOP_SESSION and found that my desktop is running in Unity-2d and I am using NVIDIA GEFORCE GT so for sure it is Optimus Technology.

Any workarounds?

I installed Nvidia-Current and ran NVIDIA-XCONFIG, instead of better results I lost screen resolution then I had to revert the XORG.conf (which I backed up before).

What is happening - Ubuntu and Nvidia?

---

### Post by UNME on 2012-07-07
Very Strange - I installed Linux Mint 13 and replaced Cinamom with Unity and it is working - Applications are stacking (like plates) and keyboard combination (including long press super key to show kbrd shortcuts).

Surely issue with Ubuntu.

---

### Post by UNME on 2012-07-07
> **unme said:**
> very strange - i installed linux mint 13 and replaced cinamom with unity and it is working - applications are stacking (like plates) and keyboard combination (including long press super key to show kbrd shortcuts).

Surely issue with ubuntu.[attach]220840[/attach]

---

### Post by UNME on 2012-07-08
I ran Mesa utils and this is what I got.
please help me further

$ glxinfo
name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0"


Also My system information

~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Ivy Bridge PCI Express Root Port [8086:0151] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.2 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 3 [8086:1e14] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1c.5 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 6 [8086:1e1a] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e57] (rev 04)
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 Mobile SATA Controller [RAID mode] [8086:282a] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0de9] (rev a1)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5229] (rev 01)
0a:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)

Any one who can help?

---

### Post by GreatDanton on 2012-07-08
For me shortcuts like super+w, work only in Unity 3D. Did you try to run in Unity 3D?

---

### Post by UNME on 2012-07-09
I am not able to switch to Unity 3d with Ubuntu 12.04 -[COLOR="DarkSlateBlue"] **this is strange**[/COLOR] [COLOR="DarkRed"]**because in Linux Mint if I replace Cinamom with Unity, shortcuts are working well.**
[/COLOR]
As my previous comment 

[COLOR="DarkSlateBlue"]**Glx. Not found**[/COLOR] - i have no idea what that means!

---

