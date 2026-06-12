---
title: "No Sound"
date: 2009-07-04
forum: General Help
---

### Post by Xoanan on 2009-07-04
Hi All

I am having a sound problem now;  I am on the ALSA mixer and have it set properly, but I have not had sound for about 2 weeks now.  Let me know what you need to know.

Thanx!:popcorn:

Here the results of lspci

```
xoanan@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
01:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
01:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI
xoanan@ubuntu:~$ 

```

---

### Post by tommcd on 2009-07-04
Try working your way through this tutorial to determine where the problem lies,; and hopefully to fix it:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Xoanan on 2009-07-04
Here's something I found using lspci -v

```
01:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
	Subsystem: Ensoniq ES1371 [AudioPCI-97]
	Flags: bus master, slow devsel, latency 64, IRQ 10
	I/O ports at df00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ENS1371
	Kernel modules: snd-ens1371

```

[COLOR="Red"]**Capabilities: <access denied>?**[/COLOR]

---

### Post by Xoanan on 2009-07-04
Here's something else I found after typing sudo modprobe snd-ens-1371
```
xoanan@ubuntu:~$ sudo modprobe snd-ens1371
[sudo] password for xoanan: 
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/libpisock9, it will be ignored in a future release.

```

---

### Post by Xoanan on 2009-07-04
Okay; I tried what the thread said;  I uninstalled and reinstalled the ASLA Mixer; rebooted and still no sound.  Its been that way since I inserted a CD that we got from the library for one of the kids pc games.  It didn't work in either Windows XP or Xubuntu.  It could be a coincidence, I suppose but still..

---

### Post by tommcd on 2009-07-04
The snd-ens1371 module is the correct one for the Ensoniq ES1371 audio chip according to the list on this page:
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)
Verify that the module is loaded on bootup by opening a terminal and running:
```

lsmod | grep -i snd

```
If you still don't have sound, try removing and reloading it:
```

sudo rmmod snd-ens1371
sudo modprobe snd-ens1371

```
Then run alsamixer again and see if you can get sound.
If that doesn't work, open: system > preferences > sound, and try changing the options from pulse audio to alsa and test. Then try changing them to OSS (if OSS is there as an option. I don't have Ubuntu running right now). 
If that doesn't work I'm not sure what else you could try.

Is the Ensoniq ES1371 the only sound card card in the computer?

---

### Post by Xoanan on 2009-07-05
Changing to OSS seemed to fix the audio issue!  Thanx!  Oh yeah, the Ensoniq is the only soundcard I have.:popcorn:

---

### Post by tommcd on 2009-07-05
Glad you got it working!
Your sound card is rather old. The driver was probably written back when OSS was the linux sound system. It may not have been updated to work with alsa, or the newer pulse audio.

Just remember that OSS may not work with more than 1 program at a time using the sound card. For example, if you are listening to mp3 files you may not hear sound in You-Tube videos at the same time. From what I remember OSS can only play 1 sound file at a time.

---

