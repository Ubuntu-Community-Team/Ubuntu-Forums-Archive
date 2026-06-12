---
title: "i dont got's no sound in ubuntu 9.10"
date: 2009-12-07
forum: General Help
---

### Post by muse3332 on 2009-12-07
hi im new to ubuntu, and i posted before but none even botherd to look so can someone give me step by step instructins, on how to do this ihave no sound i did something abotu gnome alsa mixer but it didnt work so what can i do now?

---

### Post by u.b.u.n.t.u on 2009-12-07
What operating system are you referring to when you say you have no sound?

Is the audio device on the mainboard or is the audio device a card slotted onto the mainboard?

---

### Post by muse3332 on 2009-12-07
im runnign ubuntu 9.10 and i have no idea

---

### Post by u.b.u.n.t.u on 2009-12-07
We need to determine what your audio hardware is. With that knowledge we will then we able to determine what drivers are applicable and move on from there.

Open the terminal and enter:

sudo lshw


In the report scroll down and look for "multimedia" and copy and paste that here, or just paste the entire read out.


Oh and have you checked the volume control, that it isn't set to zero?


UPDATE


Check your settings here:

System > Preferences > Sound

---

### Post by muse3332 on 2009-12-07
*-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: Rockwell International
             vendor: Rockwell International
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
             resources: ioport:d000(size=64)
what now?

---

### Post by u.b.u.n.t.u on 2009-12-07
> **muse3332 said:**
> *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: Rockwell International
             vendor: Rockwell International
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
             resources: ioport:d000(size=64)
what now?


Please read through the following post:
[http://ubuntuforums.org/archive/index.php/t-763241.html](http://ubuntuforums.org/archive/index.php/t-763241.html)

---

### Post by Davestom on 2009-12-07
Stop whinning, and start solving...! 
Dude, everyone (almost) has problems with the sound in ubuntu, and it normally takes weeks and even months to fix it (for me, in the start), but my advice is simple.

step 1) Find out what soundcard you use.. 
> lspci

step 2) google it.
[GOOGLE IS YOUR FRIEND! ]("google.com")

step 3) Find a solution yourself. :popcorn:

step 4) Good luck! Thats how I solved my problem

Hints may be:
write: > "laptop name" has no sound in ubuntu
or
write: > Problems with "Audio device" in ubuntu 
Where you in the quotes type in your audio device.

---

### Post by u.b.u.n.t.u on 2009-12-07
> **Davestom said:**
> Stop whinning, and start solving...! 


Perhaps not the best way to welcome a new member. lol

---

### Post by muse3332 on 2009-12-08
This is the last time i post about having no sound -.-i posted three times but i cant find my origanal posts but now please... i had windows xp and ubuntu dual booted then ubnutu deleted my xp so i installed ubnutu to use up all my disk so now i have no sound can someone PLEASE help me fix this prteoblem ONCE AND FOR ALL!!!

---

### Post by muse3332 on 2009-12-09
[COLOR=Lime][SIZE=5][FONT=Trebuchet MS]hi i have ubuntu 9.10 and i did 3 fresh installs so now idk what to do... does anyone have any ideas?? i have no sound at all this is the out put when i put in aplay-i [/FONT][/SIZE][/COLOR]aplay: device_list:223: no soundcards found... and this is the out put when i put in <ispci> Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
    Subsystem: ASUSTeK Computer Inc. Device 8018
    Flags: bus master, medium devsel, latency 0
    Memory at e4000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: e0000000-e1efffff
    Prefetchable memory behind bridge: e1f00000-e3ffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
    Subsystem: ASUSTeK Computer Inc. Device 8018
    Flags: bus master, stepping, medium devsel, latency 0

00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
    Flags: bus master, stepping, medium devsel, latency 32
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at d800 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via

00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
    Subsystem: First International Computer, Inc. Device 1234
    Flags: bus master, medium devsel, latency 32, IRQ 9
    I/O ports at d400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:04.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
    Flags: medium devsel
    Kernel modules: i2c-viapro

00:09.0 Multimedia audio controller: Rockwell International Device 4310
    Subsystem: Risq Modular Systems, Inc. Device 4310
    Flags: bus master, medium devsel, latency 32, IRQ 9
    I/O ports at d000 [size=64]
    Capabilities: <access denied>
    Kernel modules: snd-riptide

00:09.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
    Subsystem: Risq Modular Systems, Inc. Device 4311
    Flags: bus master, medium devsel, latency 32, IRQ 255
    Memory at df800000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: <access denied>

00:09.2 Input device controller: Rockwell International Device 4312
    Subsystem: Risq Modular Systems, Inc. Device 4312
    Flags: bus master, medium devsel, latency 0
    Memory at df000000 (32-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Riptide Joystick

00:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
    Subsystem: Hewlett-Packard Company Device 9207
    Flags: bus master, medium devsel, latency 32, IRQ 11
    I/O ports at b800 [size=256]
    Memory at de800000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too

01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
    Subsystem: ASUSTeK Computer Inc. Device 8018
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
    Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e2000000 (32-bit, prefetchable) [size=32M]
    Expansion ROM at e1ff0000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb, rivafb

---

### Post by lisati on 2009-12-09
Ouch! Hard on the eyes! (friendly teasing :) )
Which is it not getting no sound, or not getting any sound? (More friendly teasing!) :)

Have a look here: [http://ubuntuforums.org/showthread.php?t=1346644](http://ubuntuforums.org/showthread.php?t=1346644)

---

### Post by muse3332 on 2009-12-09
[color=lime]i think it would be better if someone helped me with this post cause with that other psot we dont have the same sound cards or hardware so i think it would be better if someone could helpme lol and plus im a ubntu noob[/color]

---

### Post by muse3332 on 2009-12-09
Ok my sound card isnt detected any help?

---

### Post by lisati on 2009-12-09
Did you check the link? If not, why not? And why the green text that is hard on the eyes?

---

### Post by muse3332 on 2009-12-09
LOL IDK HAHA SORRY well anyway yeah i checked the link i dont think thats my problem ive actually posted n that link lol so... i just know that my sound card sint detected help?

---

### Post by cariboo on 2009-12-09
Please do not create multiple threads about the same problem. I have merge 3 of the threads you created to form a mega thread. :)

If you don't get an answer to your question within 24 hours, it is OK to bump the thread. We would rather you do that then create multiple threads.

---

