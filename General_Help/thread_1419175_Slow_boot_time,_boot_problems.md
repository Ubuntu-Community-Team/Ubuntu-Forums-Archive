---
title: "Slow boot time, boot problems"
date: 2010-03-01
forum: General Help
---

### Post by Emperor_Muncle on 2010-03-01
I have 9.10 installed on two desktops (mine and girlfriend's), both a few years old. Mine has a slower processor, less RAM, and less space on a failing HDD. Since she is moving to a laptop, I'm taking over her computer.
However, while mine boots up in about a minute, hers takes four minutes from powering on to seeing the desktop.
Windows XP was fairly slow to load up when she had it installed, so I'm not blaming ubuntu for the problems, just hoping I'll get more help here! ;)

I wiped the computer in July when I installed Jaunty. There was always an error message with GRUB:

```
ata1: link is slow to respond, please be patient (ready=0)
ata1: SRST failed (errno=-16)
ata1: link is slow to respond, please be patient (ready=0)
ata1: SRST failed (errno=-16)
```That's not a typo, it appeared twice. This ate up about a minute

Pain, but she said she'd live with it. In an attempt to get rid of it, about a week ago I upgraded to Karmic, which removed the visible error message but did not speed up times (error is still happening, I can see it in the log). Following this, at 52 seconds, it says:

```
ata1.01: link status unknown, clearing UNKNOWN to NONE
```Afterwards, there's a pause between 55 seconds and 72 seconds.

Total time in the log: 75 seconds.  GRUB takes a long time to load, and I'm not sure where to find out what happens before GRUB loads.

The second problem: After upgrading to Karmic, it will occasionally take me to the login screen, instead of loading the profile immediately (as I want it to) When here, I cannot log in to ubuntu, and have to reboot the computer in hoping that it will log straight in (it usually does on the reboot)

Again, the log: (Ballerina is the computer, xxxxxxxxx is the username
```
Mar  1 10:12:35 Ballerina gdm-simple-greeter[1579]: WARNING: Unable to lookup user name xxxxxxxx: Success
Mar  1 11:20:04 Ballerina console-kit-daemon[663]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)'
Mar  1 11:20:04 Ballerina console-kit-daemon[663]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Mar  1 11:20:04 Ballerina console-kit-daemon[663]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Mar  1 11:20:04 Ballerina acpid: client 1523[0:0] has disconnected
Mar  1 11:20:04 Ballerina acpid: client connected from 1975[0:0]
Mar  1 11:20:14 Ballerina gdm-simple-greeter[2031]: WARNING: Unable to lookup user name xxxxxxxx: Success
Mar  1 11:20:27 Ballerina console-kit-daemon[663]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)'
Mar  1 11:20:27 Ballerina console-kit-daemon[663]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Mar  1 11:20:27 Ballerina console-kit-daemon[663]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Mar  1 11:20:27 Ballerina acpid: client 1975[0:0] has disconnected
Mar  1 11:20:27 Ballerina acpid: client connected from 2224[0:0]
Mar  1 11:20:38 Ballerina gdm-simple-greeter[2280]: WARNING: Unable to lookup user name xxxxxxxx: Success
Mar  1 11:24:23 Ballerina avahi-daemon[636]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
```To try to get over these problems, I chainloaded GRUB 2 this morning.  It actually adds more time now, since the screen has to load up and I have to pick it. At the same time, it only loads into the login screen, causing the aforementioned login problem, and forcing me to reboot and select the older GRUB.

To review: Slow to load GRUB, GRUB encounters ata1 problems, error number =-16, 
login problems

System Info:
Release 9.10
Kernel Linux 2.6.31-19 generic
Memory: 985.9 MB
Processor: Intel Celeron 2.40GHz
HDD: ATA WDC WD1600JB, 157GB Linux (0x83) partition with a 3GB SWAP

If there is a way I can reword this to make more sense, please let me know.  This is my first time posting here.

---

### Post by Emperor_Muncle on 2010-03-02
After re-reading that, I saw how wordy and complicated it was, not to mention a little presumptuous. Please let me try again:

Hi,
I've been using Ubuntu for almost a year now. Most problems I've been able to solve through a quick google search, but not this one.

Using the info I jotted down in the previous post, could somebody please suggest an idea I could explore, to try and see if I can solve my boot problems without doing an entire wipe again, or taking it to a (costly) computer repair specialist.

Thanks in advance. Most of the help for problems I've had has been found here, so I'm hoping I'll be able to find some advice for this very specific problem.

---

### Post by emanuel.b on 2010-03-02
Hmm, that's a real head scratcher... Well, I'd check the physical connection to the hard drive. Other than that, I'm at a loss. Sorry... :(

---

### Post by jpl888 on 2010-03-02
Could you post output of ```
lspci
``` and ```
uname -a
``` and I will see if I can help you.

---

### Post by jpl888 on 2010-03-02
Upon further searching and reading some potential fixes are:-

Update BIOS

Update hard drive firmware

Update kernel

Change from AHCI to IDE mode in BIOS (or vice versa)

Add "irqpoll" to kernel command line, and possibly other kernel command lines may help (I'm thinking of noioapic, noacpi, etc.)

That should keep you busy.

---

### Post by Emperor_Muncle on 2010-03-03
From lspci:
```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

```and uname

```
uname -a
Linux Ballerina 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i6
```Thanks for your other advice. I've got the day off tomorrow, I'll start on that list!

---

### Post by jpl888 on 2010-03-04
Ok well you have the latest kernel, the only obvious thing that springs to mind there is that the chipset is quite old (I think 10 years). 

It's entirely possible the mother board is just playing up anyway, although from reading bug posts, etc. about this issue it is also possible it is simply a kernel bug/regression.

You could try going back to older kernels (I thinking 2.6.28 or there abouts) to see if that helps. Add that to the list.

---

### Post by Emperor_Muncle on 2010-03-04
Well, it may be a moot point now.

I tried the first thing on the list: updating BIOS: Following the instructions here [http://ubuntuforums.org/showthread.php?t=318789&highlight=flashrom](http://ubuntuforums.org/showthread.php?t=318789&highlight=flashrom) for CD, I just rebooting the machine.
It's been running for ten minutes, no display on the monitor, HDD light still glowing away, but no actual noise.

The temptation to eject the CD, or turn off the comp is quite large. I don't think it is actually flashing the BIOS, as there hasn't been any questions, instructions or anything. Just no signal to the monitor (which is plugged in, turned on, and connected to the computer)

EDIT: Crisis averted. I reset the BIOs, and the computer is back to where it was before. Same problem, and the BIOS isn't updated, but at least it's not a pretty brick.

---

