---
title: "Help with wireless and sound"
date: 2006-06-04
forum: General Help
---

### Post by Sve on 2006-06-04
Hello all,
I've searched the forum but couldn't find any topic related to my problem.
I am absolutely new to Linux in general. I have run the Live CD on my HP Compaq 7010 laptop and it worked flawlessly (it was the 5.10 version), so I have decided to switch permanently to it. I have installed it and it worked perfect.
Then I have decided to upgrade to the 6.06 version. Everything was fine - downloaded the files and installed. After the restart though my wireless card is not working - it doesn't even show in the Networking settings! Why did this happen and is there any way I can make it work?
And another thing - my sound disappeared as well!
Any help would be grately appreciated - thanks in advance for the support!

Cheers,
Sve

---

### Post by Skye on 2006-06-04
We need some more information than that.  What wireless card do you have? What sound card do you have?

If you don't know off the top of your head, run ```
lspci -v
``` and look for entries related to sound or a wireless network card, and post them back here.

---

### Post by Sve on 2006-06-04
Hi and thank you for the reply.
I have executed the command and it returned the following:

> 0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: bus master, fast devsel, latency 0
        Memory at b0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 128
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: 90400000-904fffff
        Prefetchable memory behind bridge: 98000000-9fffffff

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 48c0 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 48e0 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 4c00 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 5
        Memory at a0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 90000000-903fffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 4c40 [size=16]
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: medium devsel, IRQ 10
        I/O ports at 4c20 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 4000 [size=256]
        I/O ports at 4880 [size=64]
        Memory at a0200000 (32-bit, non-prefetchable) [size=512]
        Memory at a0300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: medium devsel, IRQ 10
        I/O ports at 4400 [size=256]
        I/O ports at 4800 [size=128]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 01) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: bus master, stepping, 66MHz, medium devsel, latency 128, IRQ 10
        Memory at 98000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at 90400000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Flags: bus master, medium devsel, latency 128, IRQ 10
        Memory at 90200000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at 2400 [size=128]
        Capabilities: <available only to root>

0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: bus master, medium devsel, latency 128, IRQ 10
        I/O ports at 2000 [size=256]
        Memory at 90300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:02.0 Network controller: Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corp.: Unknown device 2522
        Flags: bus master, medium devsel, latency 128, IRQ 5
        Memory at 90000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: bus master, medium devsel, latency 168, IRQ 5
        Memory at 90100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001


Cheers,
Sve

---

### Post by Skye on 2006-06-04
Ok, that's good.  That listing means you have an Intel ICH4 sound card and an Intel Wireless 2100 card, both of which I think are supported.

To get your wireless working, make sure network-manager is installed (it's new in Dapper, and it's the perferred way to manage wireless things.)

```
sudo apt-get install network-manager-gnome
```

If it's already installed, it should be sitting next to your clock in the notification area in the upper right corner of the screen.  If it's not installed, install it and reboot.

See this thread for help: [http://ubuntuforums.org/showthread.php?t=186607&highlight=2100]("http://ubuntuforums.org/showthread.php?t=186607&highlight=2100")

As for the sound card, look in these threads:
[http://ubuntuforums.org/showthread.php?t=171554&highlight=ICH4](http://ubuntuforums.org/showthread.php?t=171554&highlight=ICH4)
[http://ubuntuforums.org/showthread.php?t=173953&page=2&highlight=ICH4](http://ubuntuforums.org/showthread.php?t=173953&page=2&highlight=ICH4)
[http://ubuntuforums.org/showthread.php?t=171616&highlight=ICH4](http://ubuntuforums.org/showthread.php?t=171616&highlight=ICH4)

And if none of those work, try this link:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0)

---

### Post by ericesque on 2006-06-05
I have the same audio chipset on my notebook.  This always got my sound working when I had issues... 


Open volume control (sound icon on panel). In volume control select
file>change device make sure that you have the 'IXP (Alsa Mixer)' selected.

Then go to edit>preferences
check the 'External Amplifier' option then click close.

still in the volume control there should be a new tab called 'switches'--select it.
Uncheck 'External Amplifier'
close the window and check for sound.

hope this helps.

---

