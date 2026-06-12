---
title: "Problems with drivers"
date: 2010-02-11
forum: General Help
---

### Post by JPpapa on 2010-02-11
Hi, i'm new in ubuntu and I think i have a problem with mi drivers.
Yesterday I installed ubuntu 9.10 in my pc. When i tried to activate the full visual efects i had an error ("the visual efects can't be installed") or something like that...
when i go to... System-Administration-Hardware controller (i have it in spanish so i don't know how to translate that) it appears nothing at all.
my questions:
1-Ubuntu doesn't recognice my hardware?
2-Do i need to install the PC drivers? How?
3-Would that solve my visual effects problem?
4-How can i change the idiom to english? so i can understand your advices...

Thank, hope you can help me!

---

### Post by patchwork on 2010-02-11
1.  What exactly is the hardware in question?

2.  Normally, no, PC drivers will not work (unless there is a wrapper program for it)

3.  Maybe (depends on hardware)

---

### Post by audiomick on 2010-02-11
Hallo.
In order to know if you need a proprietary driver, we need to know what hardware you have.
Open a terminal
applications> accessories> terminal
and do
```
lspci
```
i.e. type that in and hit enter.
You can copy from the terminal by selecting the text (click and move the mouse over the text) and then ctrl + shift + c
paste the result here.

---

### Post by JPpapa on 2010-02-11
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

that's all...

---

### Post by audiomick on 2010-02-11
Hi, bad news, I am afraid.
This is your graphics chip
> 01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)I found it here
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

and a quick read indicates that 3D effects (which you need for the desktop effects) can be difficult. I can't suggest anything better than to work through the page that I linked to yourself. I have nVidia graphics, and unfortunately no experience with VIA.

Good luck with it.

---

### Post by JPpapa on 2010-02-11
Well thanks, so i have to follow the instructions? and install all that? now i'll do it... then i tell you how it ended
Thanks again

EDIT: Well i have a problem in step 3.
"
**Edit the X server configuration file** 
Edit /etc/X11/xorg.conf and change the device driver to openchrome 
     gksudo gedit /etc/X11/xorg.conf"
(Go to      Section "Device"and change      
Driver             "vesa" to      
Driver             "openchrome")

When i tip  
gksudo gedit /etc/X11/xorg.conf
and press Enter it opens a .conf file that seems to be empty
[IMG]http://img251.imageshack.us/img251/6474/pantallazok.png[/IMG]

so... don't know what to do... please help

---

### Post by audiomick on 2010-02-11
hallo again.
It looks like you were following the instructions in the first half of the page. The problem is, in 9.10 there isn't an xorg.conf file by default. This method is being phased out. The method that is taking over is called randr. I can't find anything in the documentation other than the page I linked you to.

All I can suggest is to go down to the second part where it says
**[SIZE=2]> VIA proprietary graphics driver[/SIZE]**

and work through that.

There is an example of an xorg.cong file after the words
 > As an alternative to the last steps, a minimal working /etc/X11/xorg.cong file would look like this: If you do
```
gksu gedit /etc/X11/xorg.conf
```it will open a new file, as you have seen. If you copy the text from the Documentation page and paste it in there and save it, you will have a file that _might_ work. The Documentation is supposed to work for 9.04. In 9.10, if there is an xorg.conf file, that is, if you create one, it will be used. I assume that the suggested basic xorg.conf file will still work in 9.10, but I don't know.

I can not promise that this works, and can not try it on my machine.

The other option, as is also suggested in the Documentation page, would be to buy a different video card (if your computer is a desktop and not a laptop). I have nVidia, which needs the proprietary driver but works well. Or just leave the desktop effects off.

---

### Post by JPpapa on 2010-02-11
well, nothing else to do... no efects
thank for your help!

---

### Post by BSG Fan on 2010-02-12
> **JPpapa said:**
> well, nothing else to do... no efects
thank for your help!

Hello, JPpapa.
I have the same problem
did u fixed it?

I am here: 
[http://ubuntuforums.org/showthread.php?p=8814868&posted=1#post8814868](http://ubuntuforums.org/showthread.php?p=8814868&posted=1#post8814868)

---

