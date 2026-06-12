---
title: "Sound Issues - Help Would Be Appreciated"
date: 2010-08-11
forum: General Help
---

### Post by neilalwayswins on 2010-08-11
I am running** Ubuntu 10.04** and am currently having some issues with my sound. My **OS cannot seem to find my speakers or my blasted headset** (I own a Logitech G35 7.1 surround sound headset if it helps any). _*It was working before*_ but now the sound preferences just want to make my life miserable :cry:. Any help would be really appreciated as I am a Windows 7 convert and a total noob at this.

Anyway yay for linux! :p

---

### Post by ubunterooster on 2010-08-11
[SIZE=2]Paste the output of ```
aplay -l
```[/SIZE]

---

### Post by neilalwayswins on 2010-08-11
> **ubunterooster said:**
> [SIZE=2]Paste the output of ```
aplay -l
```[/SIZE]

**aplay: device_list:223: no soundcards found...**

---

### Post by ubunterooster on 2010-08-11
output of

[SIZE=2]lspci -v[/SIZE]

---

### Post by TyLLy_4 on 2010-08-11
I am having a similar problem where my mute button its "stuck on mute" please give us some more information. paste this into the terminal and report the info back here. 

also I too am a win7 convert. :) and I sure as hell don't miss Micro$$oft :D 

$ aplay -l

$ lspci -v

$ uname -a

$ cat /proc/asound/version

$ head -n 1 /proc/asound/card*/codec#*

---

### Post by neilalwayswins on 2010-08-11
> **ubunterooster said:**
> output of

[SIZE=2]lspci -v[/SIZE]
[B]00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
    Subsystem: Dell Device 02f7
    Flags: fast devsel
    Capabilities: <access denied>
\
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f8000000-fbffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:09.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 13)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
    Flags: fast devsel
    Capabilities: <access denied>

00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel modules: mce-xeon75xx

00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
    Flags: fast devsel
    Capabilities: <access denied>

00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
    Flags: fast devsel

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
    Subsystem: Dell Device 02f7
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at a400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
    Subsystem: Dell Device 02f7
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at a480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
    Subsystem: Dell Device 02f7
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at a800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20)
    Subsystem: Dell Device 02f7
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at f5600000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
    Subsystem: Dell Device 02f7
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f5df8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: c0000000-c01fffff
    Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f7f00000-f7ffffff
    Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f6000000-f7efffff
    Prefetchable memory behind bridge: 00000000c0600000-00000000c07fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f5f00000-f5ffffff
    Prefetchable memory behind bridge: 00000000c0800000-00000000c09fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f5e00000-f5efffff
    Prefetchable memory behind bridge: 00000000c0a00000-00000000c0bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
    Subsystem: Dell Device 02f7
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at a880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
    Subsystem: Dell Device 02f7
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at ac00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
    Subsystem: Dell Device 02f7
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at b000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20)
    Subsystem: Dell Device 02f7
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f5800000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
    Subsystem: Dell Device 02f7
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller (prog-if 01)
    Subsystem: Dell Device 02f7
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 33
    I/O ports at b880 [size=8]
    I/O ports at b800 [size=4]
    I/O ports at b480 [size=8]
    I/O ports at b400 [size=4]
    I/O ports at b080 [size=32]
    Memory at f5a00000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
    Subsystem: Dell Device 02f7
    Flags: medium devsel, IRQ 11
    Memory at f5dffc00 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

02:00.0 SATA controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
    Subsystem: Dell Device 02f7
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f5effc00 (64-bit, non-prefetchable) [size=128]
    Memory at f5ef8000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at cc00 [size=128]
    Expansion ROM at f5e00000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: sata_sil24
    Kernel modules: sata_sil24

03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403 (prog-if 10)
    Subsystem: Dell Device 02f7
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f5fff800 (64-bit, non-prefetchable) [size=2K]
    I/O ports at d800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

04:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)
    Subsystem: Creative Labs Device 0044
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f7ef0000 (64-bit, non-prefetchable) [size=64K]
    Memory at f7c00000 (64-bit, non-prefetchable) [size=2M]
    Memory at f6000000 (64-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: SB-XFi
    Kernel modules: snd-ctxfi

05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
    Subsystem: Dell Device 02f7
    Flags: bus master, fast devsel, latency 0, IRQ 34
    Memory at f7ff0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

09:00.0 VGA compatible controller: nVidia Corporation Device 0607 (rev a2)
    Subsystem: nVidia Corporation Device 0736
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at fafe0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidiafb, nouveau

neil@Area51:~$ \
[/B]

---

### Post by TyLLy_4 on 2010-08-11
> **neilalwayswins said:**
> **aplay: device_list:223: no soundcards found...**

I think that means that no sound drivers are installed. 
Or your sound card is non present. Did the sound work and at some point stop working or ever worked at all? 

also ... maybe try to update? 

$sudo apt-get update
$sudo apt-get upgrade

---

### Post by neilalwayswins on 2010-08-11
> **TyLLy_4 said:**
> I think that means that no sound drivers are installed. 
Or your sound card is non present. Did the sound work and at some point stop working or ever worked at all? 

also ... maybe try to update? 

$sudo apt-get update
$sudo apt-get upgrade

Here is the thing though it was working before and now its not! All my software is up to date.

---

### Post by ubunterooster on 2010-08-11
[B]This line in yours shows the audio```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
    Subsystem: Dell Device 02f7
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f5df8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```
Type ```
sudo modprobe snd-hda-intel
```
[/B]

---

### Post by neilalwayswins on 2010-08-11
> **ubunterooster said:**
> [B]This line in yours shows the audio```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
    Subsystem: Dell Device 02f7
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f5df8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```Type ```
sudo modprobe snd-hda-intel
```[/B]

[B]neil@Area51:~$ sudo modprobe snd-hda-intel
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
neil@Area51:~$ 
[/B]

---

### Post by TyLLy_4 on 2010-08-11
Nevermind ... my soulution was KDE only .... 

hope ur up and running. if sone one could help me with my issue now :( :( :(

---

### Post by neilalwayswins on 2010-08-11
There is still nothing in audio preferences. I still have no clue why my sound is busted.... I hope my sound card is working and its just my OS. ](*,)

---

### Post by ubunterooster on 2010-08-11
[B]Oops; forgot to notice your main sound card.   : P
```
04:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)
    Subsystem: Creative Labs Device 0044
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f7ef0000 (64-bit, non-prefetchable) [size=64K]
    Memory at f7c00000 (64-bit, non-prefetchable) [size=2M]
    Memory at f6000000 (64-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: SB-XFi
    Kernel modules: snd-ctxfi
```so you need to try to run```
[/B]**sudo modprobe snd-ctxfi
```**

---

### Post by neilalwayswins on 2010-08-11
> **ubunterooster said:**
> [B]Oops; forgot to notice your main sound card.   : P
```
04:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)
    Subsystem: Creative Labs Device 0044
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f7ef0000 (64-bit, non-prefetchable) [size=64K]
    Memory at f7c00000 (64-bit, non-prefetchable) [size=2M]
    Memory at f6000000 (64-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: SB-XFi
    Kernel modules: snd-ctxfi
```so you need to try to run[/B]```
**sudo modprobe snd-ctxfi**
```

OK just did that and I got the same message as the previous one...

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release. #-o

---

### Post by ubunterooster on 2010-08-11
[SIZE=2]Ugh,I'll try Alsa driver compilation```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source

```then
```
[SIZE=2]sudo dpkg-reconfigure alsa-source
[/SIZE]
```Answer yes three times then when it asks for the driver, deselect all and select the [/SIZE]**snd-ctxfi module**

---

### Post by neilalwayswins on 2010-08-11
I am stuck on this page in the terminal...

Configuring alsa-source &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Please select the ALSA sound card drivers that should be included in      &#8593; 
 &#9474; alsa-modules packages built from these sources.                           &#9646; 
 &#9474;                                                                           &#9618; 
 &#9474; The following is a list of available sound card drivers along with short  &#9618; 
 &#9474; descriptions.                                                             &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; seq-dummy (dummy MIDI-through sequencer client), dummy (dummy sound       &#9618; 
 &#9474; card), virmidi (virtual MIDI card), loopback (loopback card), ad1816a     &#9618; 
 &#9474; (ISA: Analog Devices SoundPort 1815|1816A chips), ad1848 (ISA: Analog     &#9618; 
 &#9474; Devices 1847|1848 / Cirrus Logic CS 4248 chips), adlib (ISA: FM card      &#9618; 
 &#9474; driver), ad1889 (PCI: Analog Devices 1889 (e.g. on HP PA-RISC             &#9618; 
 &#9474; computers)), ad1816a (PCI: Highscreen Sound-Boostar 16 3D), aica          &#9618; 
 &#9474; (Dreamcast AICA sound (pcm) driver), ali5451 (PCI: AC97 codec on          &#9618; 
 &#9474; motherboards with ALi M5451 Audio Controller), als100 (ISA: Avance Logic

How do I get past it?

nevermind ill just open up a new terminal thing for use :D
so...what do I do now?

---

### Post by ubunterooster on 2010-08-11
use the space bar to select and deselect up-key and down-key to navigate. Deselect "all", select **snd-ctxfi, **press enter

---

### Post by neilalwayswins on 2010-08-11
It says command not found. Did I do something wrong? ](*,)

---

### Post by ubunterooster on 2010-08-11
Did you do that in the terminal that says 

Configuring alsa-source &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Please select the ALSA sound card drivers that should be included in      &#8593; 
 &#9474; alsa-modules packages built from these sources.                           &#9646; 
 &#9474;                                                                           &#9618; 
 &#9474; The following is a list of available sound card drivers along with short  &#9618; 
 &#9474; descriptions.                                                             &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; seq-dummy (dummy MIDI-through sequencer client), dummy (dummy sound       &#9618; 
 &#9474; card), virmidi (virtual MIDI card), loopback (loopback card), ad1816a     &#9618; 
 &#9474; (ISA: Analog Devices SoundPort 1815|1816A chips), ad1848 (ISA: Analog     &#9618; 
 &#9474; Devices 1847|1848 / Cirrus Logic CS 4248 chips), adlib (ISA: FM card      &#9618; 
 &#9474; driver), ad1889 (PCI: Analog Devices 1889 (e.g. on HP PA-RISC             &#9618; 
 &#9474; computers)), ad1816a (PCI: Highscreen Sound-Boostar 16 3D), aica          &#9618; 
 &#9474; (Dreamcast AICA sound (pcm) driver), ali5451 (PCI: AC97 codec on          &#9618; 
 &#9474; motherboards with ALi M5451 Audio Controller), als100 (ISA: Avance Logic

---

### Post by neilalwayswins on 2010-08-11
No, I tried but the terminal will not let me.

---

### Post by ubunterooster on 2010-08-11
I'm confused :(

---

### Post by neilalwayswins on 2010-08-11
> **ubunterooster said:**
> I'm confused :(

OK let me try this again dangit. Thank you for your help so far. :tongue:

---

### Post by neilalwayswins on 2010-08-11
[SIZE=2] ***""select the ***[/SIZE][B]*snd-ctxfi module""*

stuck here...where is it?!
[/B]

---

### Post by neilalwayswins on 2010-08-11
I fixed my sound problem! Sorry that I took your time for something so stupidly simple. Regards

Neil

---

### Post by ubunterooster on 2010-08-11
Not a problem. :D And I came back when unable to sleep (stressfull lifestyle) and see some good news. So, you get your sound problem fixed, and I get to sleep.


We both win!

---

### Post by just12b4gotn on 2010-09-18
> **ubunterooster said:**
> Remember; mark your threads as solved

Unfortunately, I have yet to see the rocketfish/creative sound card driver issue get resolved. 
The guys reporting that alsa worked for them in a previous release has given me a speck of hope. I'll be reverting back to a previous release of alsa, then ubuntu if that doesn't work out. Then a 12 pound hammer to the mobo.

---

### Post by ubunterooster on 2010-09-18
Post the output you get when putting the following into the terminal:```
aplay -l
```[SIZE=2]
[/SIZE]

and then also that of ```
lshw
```

---

### Post by insomnia84 on 2010-11-30
Hello, 

Maybe You can help me, I have few problems with sound.
1) Problem with Secondlife stream sound (but i ll open new post about this)
2) Problem with my usb headset with mic (Logitech) - doesnt work at all
3) Problem with buit in mic on my toshiba laptop.

Lets try to deal first problem 3),
Problem is that i cant get mic to work + yesterday I had sound only on speakers and ubuntu didnt react If I connect headphones on jack (not usb).
Today I managed.. somehow to get it work on headphones, but now i have simultany sound on speakers and headphones and mic is still dead.

here is my info:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
rexi@Rexi-Satellite-A300:~$ lshw
WARNING: you should run this program as super-user.
rexi-satellite-a300       
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3962MiB
     *-cpu
          product: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:5000(size=4096) memory:d6300000-d63fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Mobility Radeon HD 3400 Series
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:48 memory:c0000000-cfffffff ioport:5000(size=256) memory:d6300000-d630ffff memory:d6320000-d633ffff
           *-multimedia
                description: Audio device
                product: RV620 Audio device [Radeon HD 34xx Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:47 memory:d6310000-d6313fff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:60e0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:60c0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:d6405c00-d6405fff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:d6400000-d6403fff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=8192) memory:d5300000-d62fffff ioport:d0000000(size=17825792)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1e:33:6f:d0:dc
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
                resources: irq:45 ioport:3000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:d4200000-d52fffff ioport:d1100000(size=16777216)
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 00:21:63:69:58:43
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=2.6.35-23-generic firmware=N/A ip=192.168.0.10 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:d4200000-d420ffff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:1000(size=4096) memory:d3200000-d41fffff ioport:d2100000(size=16777216)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:60a0(size=32)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:6080(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:6060(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:6040(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d6405800-d6405bff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:d3100000-d31fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:04:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:17 memory:d3100000-d31007ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:04:06.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:17 memory:d3100a00-d3100aff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:04:06.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:d3100900-d31009ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:04:06.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:17 memory:d3100800-d31008ff
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:6108(size=8) ioport:6114(size=4) ioport:6100(size=8) ioport:6110(size=4) ioport:6020(size=32) memory:d6405000-d64057ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d6406000-d64060ff ioport:6000(size=32)
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 82801I (ICH9 Family) Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:d6404000-d6404fff

---

