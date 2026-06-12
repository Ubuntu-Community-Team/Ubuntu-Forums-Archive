---
title: "No sound on hp 6530b"
date: 2012-06-19
forum: General Help
---

### Post by hakonma on 2012-06-19
let me starting by saying om a total noob on ubuntu, and need som help.

I got this hp 6530b that I have installed ubunto 12.04 on, and i get no sound. 

the sound card is saying its a dummy card.
and after reading all day on forums and support sites im totaly stuck. i dont know what to do. 
This is the methods that i have tried.  
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/28661](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/28661)

and when I troubleshoot by flowing this [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) all i can see from the results is that there are no driver there. and this site [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)  just get me confused.

I need this pc for a trip in 10 days, so getting some sound would be nice :P

---

### Post by Kira_Belka on 2012-06-20
hi here,
so post here results of "lspci"
and "cat /proc/asound" plz.

---

### Post by hakonma on 2012-06-20
lspci results 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
85:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
86:02.0 FireWire (IEEE 1394): LSI Corporation FW322/323 (rev 70)

cat /proc/asound results
No such file or directory

---

### Post by hakonma on 2012-06-29
is there none that can help me whit this? (i don't mean to be rod if it sounds like it. )

---

### Post by jmfal on 2012-06-29
Welcome to Ubuntu

Run this in  teminal:
```
 lspci -v      
```

Scroll down to your sound card and copy/paste that info to the code tags "#" it makes it easier to read
Before you do that click on the alsamixer link below and unmute the playback controls and increase the volumes...... play some music

---

