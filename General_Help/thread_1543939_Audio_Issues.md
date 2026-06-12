---
title: "Audio Issues"
date: 2010-08-01
forum: General Help
---

### Post by kaldor on 2010-08-01
Note: I posted this in the multimedia section, but it is getting no attention. Maybe this is a better place? I don't ask for help much :)

Been using Linux for a few years now as my sole OS (more recently a MacBook though) and one thing has always bothered me a bit; only one application seems to be able to play audio at once.

This becomes very annoying. I could be on youtube, or playing a game and not hear any of my instant messages come in because all other applications are automatically muted. People then get annoyed when I don't respond and I always need to explain "my audio cut out or something". I can't listen to music while I play a game either; it's one or the other. 

This isn't only Ubuntu. All distros I have ever used have this issue as well.

What should I do?

---

### Post by themusicalduck on 2010-08-01
You only posted your other thread 25 minutes ago :P can't always expect a reply that quickly ;)

Are you on Ubuntu 10.04 and is everything default? You haven't removed anything to do with pulseaudio or installed other sound drivers? The only time I had problems with that was on older versions of Ubuntu (like 8.04) and when trying to use OSS.

Have you set any applications to use OSS instead of ALSA? As that application in particular might be blocking things. Especially since you mention games. If you are playing a game on Wine and Wine is set to use OSS then it will block other applications from using sound.

---

### Post by kaldor on 2010-08-01
Yes, everything is default on 10.04. 

The games I play are mostly native using PulseAudio I believe. Only one game is on Wine. But it is also when using Flash or Java as well. When I took an online course I couldn't have Skype or Pidgin open, because the teacher would be muted :(

---

### Post by themusicalduck on 2010-08-01
What model PC do you use? Type lspci into a terminal (Applications > Accessories > Terminal) and post the output here (within CODE tags).

---

### Post by kaldor on 2010-08-01
> **themusicalduck said:**
> What model PC do you use? Type lspci into a terminal (Applications > Accessories > Terminal) and post the output here (within CODE tags).

lspci returns my Sound card as follows: 

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

Full output:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

The sound quality is wonderful apart from the issues I noted.

---

### Post by lidex on 2010-08-01
Scroll down to this section - Multiple Application Sound Sharing - here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

Have a look here also:
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by kaldor on 2010-08-03
> **lidex said:**
> Scroll down to this section - Multiple Application Sound Sharing - here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

Have a look here also:
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Didn't really help at all; there were no instructions.

---

