---
title: "Sound quit working"
date: 2009-11-24
forum: General Help
---

### Post by iamgeniusrnti on 2009-11-24
Ok so I ran this script (shown here [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)) out of my home dir to try to get my microphone working and now I have no sound at all.

It just boots up and mutters something about alsa module not working, falling back to pulse audio and I have no sound at all.

I tried reinstalling alsa from synaptics with no dice.

Here is my lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

Is there a way to get the sound card redetected?  It works fine during install.  I can live without the mic I guess:)

---

### Post by iamgeniusrnti on 2009-11-24
Oh yea... when I run the bash2 script, it says it can't stat the dir.  There are driver folders in my home dir which was placed there by the 1st script.

---

### Post by Julita on 2009-11-24
You might find it useful: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by iamgeniusrnti on 2009-11-24
> **Julita said:**
> You might find it useful: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Errm... yea, the first link actually looked like it was on to something but it didn't work completely--as a matter of fact I felt silly afterwards.

I did this next: [http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/mic-issue-with-acer-aspire-one-10-in-ubuntu-unr-729158/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/mic-issue-with-acer-aspire-one-10-in-ubuntu-unr-729158/)

That finally worked somewhat... now it says Alsa device didn't work and falling back to OSS.

If I run alsamixer, I now get this:
alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB, version ALSA_0.9 not defined in file libasound.so.2 with link time referenc
Only one guy reported that back in 2007, begged for help and the Linux Gods muted him by shutting down his thread... probably killed him too, as the guy never spoke again.

Don't know what OSS is, probably an antiquated sound driver but it can mp3s again so I will keep that and pretend alsa works!

---

