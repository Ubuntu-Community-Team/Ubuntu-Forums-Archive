---
title: "Persistent Sound Problems"
date: 2010-09-03
forum: General Help
---

### Post by amanisdude on 2010-09-03
Hi everyone,

In recent months, I have become incredibly frustrated with Ubuntu.  Don't get me wrong, I love the idea of an open source operating system and, in most respects, Ubuntu has worked flawlessly.  However, with others, I've seemed to have had more problems with Ubuntu than I've ever had with even Windows Me!

Anyway, in my latest string of problems, I have been unable to get my sound in Ubuntu working correctly.  I have followed ALL the steps in the Community [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") page, the [Sound Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") forum post, and the [Ubuntu Wiki]("https://wiki.ubuntu.com/DebuggingSoundProblems"), among many other troubleshooting instructions and forum posts.  I've even completely purging ALL my sound-related software and reinstalling, but no luck.

The problem I've been having is one that seems to plague many Ubuntu users, but whose solution seems to be relatively undocumented, if it exists.  That is, the sound often seems to stop working when a continuous audio stream is active or when a video stream is running (flash, mpeg, ogg, you name it).  This is even apparent in the Ubuntu startup, where the default startup theme is often choppy on load (though I attribute this particular instance to be due to high CPU usage on startup.)

I've spent a LOT of meticulous time trying to figure out EXACTLY what is causing it, and I'm only taking to these forums after MONTHS of research and failed investigation.  It doesn't necessarily seem to be a CPU-activity related error, as the sound often will cut out just playing MP3 or WAV files with almost no CPU usage.  

On the other hand, it doesn't really seem to be a specific software-related error, as uninstalling PulseAudio or reinstalling ALSA seems to have little-to-no effect on the problem.  To date, no program has been immune from this error.

Once the sound cuts out, it takes some time for it to start up again, or it does NOT restart on its own unless some other action is done.  For example, playing an OGV file in VLC Media Player or a Flash stream with flashplayer-nonfree will often result in the audio cutting out while the video is still running.  Then, at some point, the audio will start up again, but the video, which is now minutes ahead, will freeze until the audio catches up.  Alternatively, the audio will NOT restart until I do something seemingly unrelated, like open a new tab in Chrome.  

Another possible error is that the sound will cut out completely, and then my computer will PLAY ALL THE SOUNDS that have not been played LONG AFTER I've closed the game or program, often when I am shutting down.  This leads me to believe that this may be some kind of audio buffer access error.

Anyway, I hope that posting this problem will generate some ideas, and especially some solutions.  I've been wracking my brain over it for the better part of three months.  Any ideas/criticisms are welcome, and I hope you have better luck with this than me!

Below I've posted the output dump of several programs which might help troubleshoot the error.  I may have gone a bit overboard in this regard, but I feel that any additional bit of information that might help generate a solution is worth the redundancy.  :D  So, here it goes!:

Output of [FONT="Courier New"]aplay -l[/FONT] :```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Output of [FONT="Courier New"]lspci -v[/FONT] :```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface
	Flags: bus master, fast devsel, latency 0
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
	Subsystem: Gateway 2000 Device 4043
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
	Flags: fast devsel
	Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
	Subsystem: Gateway 2000 Device 4043
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at c400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
	Subsystem: Gateway 2000 Device 4043
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at c800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
	Subsystem: Gateway 2000 Device 4043
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at cc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
	Subsystem: Gateway 2000 Device 4043
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Gateway 2000 Device 4043
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ffa7f400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: ff800000-ff8fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Device 4043
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at 40000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Gateway 2000 Device 4043
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at e800 [size=8]
	I/O ports at e400 [size=4]
	I/O ports at e000 [size=8]
	I/O ports at dc00 [size=4]
	I/O ports at d800 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Gateway 2000 Device 4043
	Flags: medium devsel, IRQ 17
	I/O ports at d400 [size=32]
	Kernel driver in use: i801_smbus
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Gateway 2000 Device 4043
	Flags: bus master, medium devsel, latency 0, IRQ 17
	Memory at ffa7fc00 (32-bit, non-prefetchable) [size=512]
	Memory at ffa7f800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
	Subsystem: Gateway 2000 Device 4043
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at ff8ff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at bc00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100
```

Output of '[FONT="Courier New"]/etc/modules[/FONT]' file:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
snd-intel8x0

# Generated by sensors-detect on Thu Jul 15 00:59:47 2010
# Adapter drivers
i2c_i801
# Chip drivers
lm85
max6650
```

Output of '[FONT="Courier New"]/proc/asound/modules[/FONT]' file:```
 0 snd_intel8x0
```

Output of [FONT="Courier New"]cat /etc/modprobe.d/alsa-base[/FONT] :```
cat: /etc/modprobe.d/alsa-base: No such file or directory
```

Output of [FONT="Courier New"]grep 'audio' /etc/group[/FONT] :```
audio:x:29:pulse,amanisdude
```

Output of '[FONT="Courier New"]/proc/asound/cards[/FONT]' file:```
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC202 at irq 17
```

Complete output of [FONT="Courier New"]lspci[/FONT] :```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
```

Those are all the outputs I can think of.  If you think I should include any more information, don't hesitate to request it.  Anyway, thanks, all for any help, and I wish you the best of luck!  :D

---

### Post by Vigh on 2010-09-03
I have had some problems with sound, but everything is working now. Firstly try install alsa-base and linux-sound-base. It looks like you dont have the required alsa-base files.

sudo apt-get install linux-sound-base alsa-base alsa-utils

You could then try compiling the latest version of alsa and pulse-audio from source which is what I did.

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

u need- 
alsa-driver
alsa-lib
alsa-utils

and possibly some additional packages for the system which may be missing in order to compile these 3 packages

extract the 3 packages
open terminal
cd to each directory that you extracted
type ./configure
sudo make
sudo make install
for each directory

you can also try putting the latest pulse-audio on
i used this guide- [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
admittedly its supposed to be automatic with versions higher than 8.04 but i followed this guide, the configuration files and packages seemed to be missing for some reason after i updated

basically u need to 
open terminal
type-

sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

gksudo gedit /etc/asound.conf (you may already have this file, but if it opens blank add the following lines in and save)

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

restart and hope for the best!

I basically just read and read and tweak settings until everything works. Which except for my intel video card, everything is running fantastic now on my laptop.

You have already tried all of this. Then I apologize.
Good-luck

forgot to say- open a terminal
type sudo alsaconf
select your soundcard

type alsamixer
check that all the volumes are turned up! they are set to mute by default

---

### Post by amanisdude on 2010-09-05
Hi Vigh,

Thanks for your reply!  I've recompiled and reinstalled the software you listed, and it has seemed to have made some difference.  It's not perfect, but it's certainly better than it used to be.

I still have to restart my computer after installing/reinstalling the PulseAudio-related software and updating asound.conf, so we'll see what happens after reboot.  I suspect, though, that it won't make much of a difference.  The sound problem is consistent across all my various installations of Linux on this same machine, so I'm fairly certain that this is a hardware compatibility-related issue.  

At any rate, I have a fairly old CPU (Pentium IV) and audio architecture, so I'm not sure how much of a priority its compatibility is for developers, so we'll see if the upcoming releases of ALSA or PulseAudio fix this.

Thanks, again!

---

### Post by ulnsterile on 2010-09-06
good day everyone, im using lucid lynx and im having a bit problem with my soundcard, after installing the sound card (intex) and disabling the onboard audio (disabled on BIOS too) the sound on mp3s stutters then cuts out after 1 minute of playback. on you tube it has no sound. if i enable the onboard audio there's no problem. i tried all the workarounds shown on ubuntu forums and still can't figure this out. still unable to get a fix. help!!!!
 i really appreciate it if somebody out there can give me a fix. thanks in advance to every one. rock ON!!

---

### Post by amanisdude on 2010-09-07
Hi ulnsterile,

I had pretty much this same problem, except it did get progressively better following the suggestions on the community boards, though it was not completely solved.

You may have already done so, but if you haven't, try the suggestions in the following links:
-[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
-[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
-[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

If none of these help, I recommend you post the output of the following terminal commands so the good people of this community can further assist you:

[FONT=Courier New]aplay -l[/FONT]
[FONT=Courier New]lspci -v[/FONT]
[FONT=Courier New]lshw[/FONT]
[FONT=Courier New]cat /etc/modules[/FONT]
[FONT=Courier New]cat /proc/asound/modules[/FONT]
[FONT=Courier New]cat /etc/modprobe.d/alsa-base[/FONT]
[FONT=Courier New]cat /proc/asound/cards[/FONT]

[FONT=Courier New][FONT=Verdana]Also, be sure that each of your users are added to the [FONT=Courier New]audio[/FONT] group.  (Go to 'System' > 'Administration' > 'Users and Groups', click '_M_anage Groups', select 'audio' from the list of groups, click _'P_roperties', and look under "Group Members").  

Hope some of this helps!

_______________________
-*amanisdude*

[/FONT][/FONT]

---

