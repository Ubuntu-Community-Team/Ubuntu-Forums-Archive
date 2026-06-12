---
title: "Loaded Linx, Dual monitor setup help"
date: 2010-06-19
forum: General Help
---

### Post by JAS510 on 2010-06-19
Hello,

I loaded Lucid on my system, dual booting w/ win7.  I have two monitors, and i need it to have extended desktop view.  How do i enable this? 
here is my LSPCI

00:08.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
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
**02:00.0 VGA compatible controller: nVidia Corporation G92 [Quadro FX 3700] (rev a2)**
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
..

right now my monitor dislay is not want i wanted. 

Please help...

---

### Post by twisted_steel on 2010-06-19
Do you know if you are using the video drivers from nvidia?  You should be able to check with (from the terminal):

```
lsmod | grep nvidia
```

This is the output on my desktop:

```
user@hostname:~$ lsmod | grep nvidia
nvidia              10832442  40
```

If so, you can set up dual monitors with the Nvidia program (nvidia-settings).  I don't believe it comes installed by default.  Once it is installed, open up the settings window with

```
gksudo nvidia-settings
```

It will also show up in the system menu, but for some reason never launches with enough permissions to save the file.  Go to X Server Display Configuration and you are looking to set up TwinView.  Once you have everything set up, save the X configuration file (button in the bottom right).  I believe you can test it out by applying the changes.  If not, it may require a reboot.

---

