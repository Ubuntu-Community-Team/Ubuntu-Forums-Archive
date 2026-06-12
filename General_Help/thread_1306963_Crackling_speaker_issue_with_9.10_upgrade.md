---
title: "Crackling speaker issue with 9.10 upgrade"
date: 2009-10-30
forum: General Help
---

### Post by Moruix on 2009-10-30
Hi all, I've recently upgraded to karmic and everything works perfect, except for the fact the speakers emit a crackling sound before and after I play any type of audio, and it also cracks when I adjust the volume meter. 

I guess I should be thankful I have sound but its so annoying!

Any ideas?

Thanks

---

### Post by blumf on 2009-10-30
Similar problem too.

Crackling noise on headphones when no audio played (can't hear anything on speakers but may be too quiet). As soon as audio is played the crackling stops but returns a second or so after playback ends.

Tried muting the mic in but no effect.

It looks like a regression as previous version of Ubuntu didn't do this.

Intel HDA chipset

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
```

---

### Post by Moruix on 2009-10-30
I'm sorry, heres my lspci


```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
andy@andy-laptop:~$ 

```

---

### Post by lovinglinux on 2009-10-30
[http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12)

---

### Post by blumf on 2009-10-30
> **lovinglinux said:**
> [http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12)

That worked for me, thanks.

---

### Post by Moruix on 2009-10-30
> **lovinglinux said:**
> [http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12)

Thanks so much! This solved my issue!

---

### Post by Kinetic1001101 on 2009-10-30
I have this problem too when I upgraded..   ??

---

### Post by Moruix on 2009-10-30
> **Kinetic1001101 said:**
> I have this problem too when I upgraded..   ??


Try to put a # in front of the last line in the /etc/modprobe.d/alsa-base.conf

---

### Post by Capt. Blackwood on 2009-10-30
That's not working, and my card is a Creative SB X-Fi

---

### Post by deputyjones on 2009-10-30
Same here with Creative Audigy gamer card. Actually not the same. Mine crackles all the time.

---

### Post by deankovell on 2009-11-04
thanks lovinglinux

---

### Post by Aerodynamic on 2009-11-04
[]("http://swiss.ubuntuforums.org/member.php?u=278151")Audio device: Intel Corporation 82801G (ICH7 Family) High Definition AudioController (rev 01)

Have the same problem, solved after commenting the line #options snd-hda-intel power_save=10 power_save_controller=N in the file /etc/modprobe.d/alsa-base.conf

thanks BXCracer =)

---

### Post by p1977p on 2009-11-10
Worked like a charm...... Thanks a lot!!!!:D

---

### Post by Drumber on 2009-11-10
I'm also having this problem. The file is read-only though, how do I save the changes?

---

### Post by deankovell on 2009-11-13
> **Drumber said:**
> I'm also having this problem. The file is read-only though, how do I save the changes?
open terminal:  ~$sudo gedit /etc/modprobe.d/alsa-base.conf

---

### Post by Drumber on 2009-11-16
> **deankovell said:**
> open terminal:  ~$sudo gedit /etc/modprobe.d/alsa-base.conf

Thanks alot, although this didn't fix my problem. I can reduce the crackling if I turn down the mic and line in volumes on aumix, and the crackling only seems to effect the front headphone socket (not the rear one for the speakers). Any other suggestions?

---

### Post by Andrew Womack on 2009-11-19
I too had the crackling speaker issue.  I opened the alsamixer from terminal and muted the "CD" playback.  This solved the crackling issue completely.  Could someone inform me as to what this playback actually is?  I suspect it is from the days when CD drives had speaker jacks located on their front panels, which of course mine do not.

---

### Post by RichyL on 2009-11-20
Initally my Audigy card was not working in 9.10 (although it did in 9.04) so first I went to Applications>Sound & Video> Gnome ALSA Mixer. Found the tab Sigmatel STAC9750,51 and ticked "Audigy Analog/Digital Output Jack" so it was on.

Then I got sound but it was all crackly. :-(

Had a play about and in the end all I had to do was to go to System>Preferences>Sound>Hardware (tab).

In the drop down box I selected "Analog Surround 4.0 Output". One thing I noticed as I worked my way through the options is that "Analog Mono Output + Digital Stereo (IEC958) Input" nearly blew my ears out (I use headphones) so BE CAREFUL.

Now I've sound working and the good thing for me is that the nVidia restricted drivers would not work for me in 9.04 but they do now so I've got wobbly windows and music. Awesome!

---

### Post by linuxgeek77 on 2009-11-23
trythis post: i have posted a sloution for you. and every1 who is using HDA card. on a laptop or desktop. [http://ubuntuforums.org/showthread.php?t=1335045](http://ubuntuforums.org/showthread.php?t=1335045)

---

### Post by thegodsquirrel on 2009-12-22
> **lovinglinux said:**
> [http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12)

Thank you for the post!!!  Finally I am snap crackle and pop free!!!

---

### Post by llawwehttam on 2009-12-22
> **Andrew Womack said:**
> I too had the crackling speaker issue.  I opened the alsamixer from terminal and muted the "CD" playback.  This solved the crackling issue completely.  Could someone inform me as to what this playback actually is?  I suspect it is from the days when CD drives had speaker jacks located on their front panels, which of course mine do not.

haha mine still have speaker jacks on them. I have 2 dvd/RW drives with jacks on them and they still haven't broken so I haven't replaced them.

---

