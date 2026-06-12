---
title: "Sound not working - HELP!!"
date: 2010-02-15
forum: General Help
---

### Post by NewToLinuxAIR on 2010-02-15
Hi 

I have a desktop pc which is running Ubuntu 9.10, and for some apparent reason I am not getting sound from my sound card. No error message is coming from o/s, I have checked the sound card with head phones, still no sound.

Now, I have checked my sound card, because on the same desktop pc, I have another hard drive, which runs Windows XP Professional, and my sound card works perfectly! Please note that I have two hard drives on my pc, one for Ubuntu and the other for XP. So, there is no conflict on operating systems.

Does anyone know how I can resolve my sound problem - my sound card is a Creative Audigy 2 Sound Blaster.

Thanks

---

### Post by RedSingularity on 2010-02-15
In a terminal type

alsamixer

and make sure all the volumes are up.

---

### Post by paulmmj on 2010-02-15
Restart your computer, and hit F2 or F10 or whatever to go into "BIOS," and make sure your "System Speaker" is "Disabled." It may be worded differently, but that'd be the jist of it. The system speaker is what makes that obnoxious BEEP noise when you hit a key and don't let go, you wont miss it, haha. That's what fixed mine.

---

### Post by mhgsys on 2010-02-15
Kindly try this;


open a terminal; typ
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

change the line

```
options snd-hda-intel power_save=10 power_save_controller=N
```

into

```
options snd-hda-intel power_save=0 power_save_controller=N
```

reboot;


[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/442463](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/442463)

---

### Post by NewToLinuxAIR on 2010-02-15
I typed in alsamixer, these are the results:

Master:100
Tone: MM
Bass: 50<>50
Treble: 50<>50
3D Contr: 0
PCM Cent: 100
PCM Fron: 100<>100
PCM LFE: 100

I had volumne on the control turned right up, and it no difference

---

### Post by NewToLinuxAIR on 2010-02-15
It is already disabled.

---

### Post by RedSingularity on 2010-02-15
Post the output of 

aplay -l

---

### Post by NewToLinuxAIR on 2010-02-15
Is this a terminal command, because if it is, nothing came out?

---

### Post by NewToLinuxAIR on 2010-02-15
Nothing happened

---

### Post by RedSingularity on 2010-02-15
Well thats no good..................That means that the system is not seeing the actual sound card.

Post the output of 

lspci

Maybe we can find the sound card in there.

---

### Post by NewToLinuxAIR on 2010-02-16
Hi 

Sorry for the delay in replying, but as you might have noticed, I live in the UK. So, there is a bit of a time difference.

Anyhow, I took a screen dump for you, and here is the output:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:01.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:04.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
05:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a1)

---

### Post by RedSingularity on 2010-02-16
In a terminal try this

sudo modprobe snd-hda-intel

Then see if you have sound.

---

### Post by NewToLinuxAIR on 2010-02-17
Hi

I typed in the command into the terminal console, and then tried playing some sounds, but nothing was heard.

---

### Post by RedSingularity on 2010-02-17
OK try this

sudo modprobe snd-intel8x0

Then try your sound again.

---

### Post by RedSingularity on 2010-02-17
Oh and when you try doing these make sure your volume is all the way up by typing 

alsamixer 

into the terminal and checking the levels there.

---

### Post by NewToLinuxAIR on 2010-02-18
Nope. That didn't work either.

Found this yesterday:
[http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/](http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/)

Is worth trying what's in the above link?

---

### Post by RedSingularity on 2010-02-18
Those two commands i gave you (snd-hda-intel) (snd-intel8x0) were the ones for your sound card.  (Intel).  If those didnt work i am not sure what you can do next so you might as well try it..........but first post the output of 

lspci -v

so i can confirm your sound card manufacturer.

---

### Post by NewToLinuxAIR on 2010-02-18
Hi,

Thanks for your reply.

Here is another dump for you:

andy@andy-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8178
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: ddf00000-dfffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 81a0
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at ddbf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: dde00000-ddefffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: ddd00000-dddfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 5000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 5400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 6000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at ddbff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00008000-0000afff
	Memory behind bridge: ddc00000-ddcfffff
	Prefetchable memory behind bridge: 0000000080000000-00000000800fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 2601
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 23
	I/O ports at 7800 [size=8]
	I/O ports at 7400 [size=4]
	I/O ports at 7000 [size=8]
	I/O ports at 6800 [size=4]
	I/O ports at 6400 [size=16]
	Memory at ddbffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: medium devsel
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs Device 1007
	Flags: bus master, medium devsel, latency 64, IRQ 22
	I/O ports at 8800 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

01:01.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
	Subsystem: Creative Labs Device 0060
	Flags: bus master, medium devsel, latency 64
	I/O ports at 9000 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp

01:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10)
	Subsystem: Creative Labs Device 0010
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at ddcdf000 (32-bit, non-prefetchable) [size=2K]
	Memory at ddcd4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 808b
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at ddcdf800 (32-bit, non-prefetchable) [size=2K]
	Memory at ddcd8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

01:04.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device 8138
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at a800 [size=8]
	I/O ports at a400 [size=4]
	I/O ports at a000 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9400 [size=16]
	Expansion ROM at 80000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: pata_it821x

02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 819f
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at dddffc00 (64-bit, non-prefetchable) [size=128]
	Memory at dddf8000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at b800 [size=128]
	Expansion ROM at ddd00000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: sata_sil24

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
	Subsystem: ASUSTeK Computer Inc. Device 8142
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at ddefc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at c800 [size=256]
	Expansion ROM at ddec0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

05:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 81f6
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at df000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at de000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at e800 [size=128]
	[virtual] Expansion ROM at ddfe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

I am very worried, because I don't particularly want to do a complete reformat and install!!

Look forward to hearing from you!

---

### Post by RedSingularity on 2010-02-18
Ok it looks like you are using the intel driver already.  Try the following.

modprobe snd-hda-intel

then in terminal

alsamixer 

to check the volume levels.  

Try if still no sound do this

sudo apt-get autoremove --purge pulseaudio

Reboot and try your sound again.

---

### Post by NewToLinuxAIR on 2010-02-20
Nope! That didn't work, either.

Anyhow, if you recall I sent you a link, I found. Well, I installed the GNOME Alsa Mixer. After installing the mixer, I selected Audigy option - guess what - my sound came back. Then I added the pulse package, and my sound is now fine. 

However, I have another problem, when I select sound from preferences, I get a message box saying "Waiting for sound system to respond" click cancel. How do I get this back, and as in the link I was able to install "Default Sound Chooser". The error I was getting even though I was in the folder that contained the package was that there was no such package. 

Any ideas?

---

### Post by RedSingularity on 2010-02-20
I never used the Gnome alsa mixer.......i have always used the default "alsa mixer" in the terminal so i cant be of any help in this matter.  Sorry.  I suggest you start a new thread that way more people will respond.

---

### Post by MooPi on 2010-02-20
You have two sound devices installed. I'm going to assume that the intel sound device is a motherboard integrated device. You may want to disable this through the BIOS so it doesn't interfere in the future.

---

### Post by zipperback on 2010-03-11
Some computers have separate audio ports for speakers and head phones.

For example, on my laptop I have a dedicated head phone port and a dedicated speakers port.

If this is the case on your computer, plug in a set of head phones into the head phone port and see if there is sound coming from that port.

- zipperback
:popcorn:

---

