---
title: "Get the sound to work on Ubuntu 10.04 Minimal install"
date: 2010-08-17
forum: General Help
---

### Post by Gorilllanobaka on 2010-08-17
[FONT=Arial]Right ..Looks like my Linux-fu skills are not as good as i thought they are..:grin:

I am currently working on a minimal install for my underpowered 7 years old laptop..

I had tried the to do the same thing before but using a server install cd instead....Worked perfectly but no sounds....

After a lot of reading i found out that the servers are not supposed to have sound and all that (Which make a lot of sense ) ,so back to the square one!!

Again I have installed on my low-spec'ed computer a minimal install using Ubuntu 10.04 Minimal CD Image this time and here is what i did so far: 

As soon as i had the CLI Ubuntu installed i went trough this steps:


sudo apt-get update

sudo apt-get install xorg xterm icewm menu gksu synaptic --no-install-recommends rox-filer my seamonkey browser , flash conky alsa-base alsa-utils alsa -oss linux-sound-base

Afterwards i sudo usermod -a -G audio myself

And i tried to run alsaconf (Spoiled by Puppy Linux) of curse it did not worked and after doing some serious reading i found out the reason why...

I run a alsamixer un-muted everything  pop-ed up the volume to the max (On all the devices)

I sudo alsactl init  then rebooted and tried to test my sound..No joy...:sad:

Right now i am kinda stuck I have no other idea what do do next in order to get the sound working...

Looks like there is something i do wrong but i`ll be damn if i understand what..

(Reading the effing manual it did not helped in my case as my gorilla brain is just to thick to make make it work...:grin:)


So... the million $ question is ..what I am doing wrong ???


Thanks in advance


PS: I would really like to make it work because i love how little RAM this setup uses..

Here`s a screen shot ...Please ignore the messed up conky (I am still working on it..)
Look instead at the uptime, load, and the ram usage and you will see why i would really like to make it work..

Cheers!


[IMG]http://i36.tinypic.com/m9vt5y.jpg[/IMG]
[/FONT]

---

### Post by jmfal on 2010-08-17
Welcome to ubuntu.

open a terminal:

       ```
 aplay -l
```

this should list your sound device.  and

          ```
   lspci -v
```

this will tell you the kernel and soundmodule in use

To be honest I haven`t messed with the minimal version, let`s give that a try

post the results and work from there

---

### Post by Gorilllanobaka on 2010-08-17
jmfal...thank you  for your help ...


Here we come...


[PHP]
root@Gorilla:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@Gorilla:~# 


[/PHP]
And the other one...
[PHP]

00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
    Subsystem: NEC Corporation Device 824c
    Flags: bus master, 66MHz, medium devsel, latency 64
    Memory at e0000000 (32-bit, prefetchable) [size=64M]
    Memory at dc000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [a0] AGP version 3.0
    Kernel driver in use: agpgart-ati
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
    Flags: bus master, 66MHz, medium devsel, latency 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: dc100000-dc1fffff
    Prefetchable memory behind bridge: e4000000-e7ffffff
    Kernel modules: shpchp

00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01) (prog-if 10)
    Subsystem: NEC Corporation Device 824c
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
    Memory at dc001000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01) (prog-if 10)
    Subsystem: NEC Corporation Device 824c
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
    Memory at dc002000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01) (prog-if 20)
    Subsystem: NEC Corporation Device 824c
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
    Memory at dc003000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SMBus (rev 18)
    Subsystem: NEC Corporation Device 824c
    Flags: 66MHz, medium devsel
    I/O ports at 8060 [size=16]
    Memory at dc004000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: NEC Corporation Device 824c
    Flags: bus master, medium devsel, latency 64, IRQ 11
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8070 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc Device 434c
    Subsystem: NEC Corporation Device 824c
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=0a, sec-latency=68
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: dc200000-dc2fffff
    Prefetchable memory behind bridge: 40000000-47ffffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
    Subsystem: NEC Corporation Device 8244
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 10
    Memory at dc004400 (32-bit, non-prefetchable) [size=256]
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
    Subsystem: NEC Corporation Device 8247
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 10
    Memory at dc004800 (32-bit, non-prefetchable) [size=256]
    Kernel driver in use: ATI IXP MC97 controller
    Kernel modules: snd-atiixp-modem

01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
    Subsystem: NEC Corporation Device 8246
    Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
    Memory at e4000000 (32-bit, prefetchable) [size=64M]
    I/O ports at 9000 [size=256]
    Memory at dc100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at dc120000 [disabled] [size=128K]
    Capabilities: [58] AGP version 3.0
    Capabilities: [50] Power Management version 2
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon

02:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b1)
    Subsystem: NEC Corporation Device 824c
    Flags: bus master, medium devsel, latency 168, IRQ 11
    Memory at dc202000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 48000000-4bfff000
    I/O window 0: 0000a400-0000a4ff
    I/O window 1: 0000a800-0000a8ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b1)
    Subsystem: NEC Corporation Device 824c
    Flags: bus master, medium devsel, latency 168, IRQ 10
    Memory at dc203000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
    Memory window 0: 44000000-47fff000 (prefetchable)
    Memory window 1: 4c000000-4ffff000
    I/O window 0: 0000ac00-0000acff
    I/O window 1: 00001400-000014ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:0a.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 06) (prog-if 10)
    Subsystem: NEC Corporation Device 824c
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at dc200000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:0a.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 15)
    Subsystem: NEC Corporation Device 824c
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at dc200800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

02:0a.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 06)
    Subsystem: NEC Corporation Device 824c
    Flags: medium devsel, IRQ 11
    Memory at dc200c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2

02:0a.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 01)
    Subsystem: NEC Corporation Device 824c
    Flags: medium devsel, IRQ 11
    Memory at dc201000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2

02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: NEC Corporation Device 8249
    Flags: bus master, medium devsel, latency 64, IRQ 10
    I/O ports at a000 [size=256]
    Memory at dc201400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp



[/PHP]

Thanks...

---

### Post by jmfal on 2010-08-17
Lets try some simple things

rightclick on speaker icon on top panel choose preferences, and see if there is a default sound card. If there is no icon go to system>preferences>sound right click add to panel.

If you there are no choices there, open sound (left click), click hardware>profile dropdown arrow and make sure it`s not turned off, you can try analog stereo duplex or one that say`s ac97, you might have to play with it.

in same window click output, put a check in box if not checked already, turn up volume
try playing some music.

try this I`ll be here for about an hour (work)

---

### Post by jmfal on 2010-08-17
If you have sound great, if not try in a terminal

       ```
 sudo modprobe snd-
```

hit enter, enter your password type command again, then hold down tab key hit enter

and a list of sound modules will appear. look for snd-atiixp   if its there enter this

           ```
   sudo modprobe snd-atiixp
```

if that doesn`t do anything put a space between the - and a

if that does`t work read the stickies in the multimedia/video section of the forum

when you get your sound going mark it solved and try to explain what you did, maybe it will help others

good luck

---

### Post by Gorilllanobaka on 2010-08-17
> **jmfal said:**
> Lets try some simple things

rightclick on speaker icon on top panel choose preferences, and see if there is a default sound card. If there is no icon go to system>preferences>sound right click add to panel.

If you there are no choices there, open sound (left click), click hardware>profile dropdown arrow and make sure it`s not turned off, you can try analog stereo duplex or one that say`s ac97, you might have to play with it.

in same window click output, put a check in box if not checked already, turn up volume
try playing some music.

try this I`ll be here for about an hour (work)


Right... first of all this is not gonna work...I am not using Gnome but ICEWM ..I mean the whole point of the stuff is to avoid installing 500 MB of unwanted stuff...

[IMG]http://i35.tinypic.com/9bm54k.jpg[/IMG]


Looks like will have to do it from the terminal (Fine by me..)

Once again thanks for your help

---

### Post by Gorilllanobaka on 2010-08-17
> **jmfal said:**
> If you have sound great, if not try in a terminal

       ```
 sudo modprobe snd-
```hit enter, enter your password type command again, then hold down tab key hit enter

and a list of sound modules will appear. look for snd-atiixp   if its there enter this

           ```
   sudo modprobe snd-atiixp
```if that doesn`t do anything put a space between the - and a

if that does`t work read the stickies in the multimedia/video section of the forum

when you get your sound going mark it solved and try to explain what you did, maybe it will help others

good luck



Here we go... for the first command    modprobe snd-..

[IMG]http://i37.tinypic.com/6gwgzo.jpg[/IMG]


And for the second one....  modprobe snd-atiixp  well, the second one it does not do anything at all ..But i guess that was to be expected

[PHP]
root@Gorilla:~# modprobe snd-atiixp
root@Gorilla:~# 

[/PHP]Cheers

---

