---
title: "temporary hangs with HDD light on"
date: 2011-05-04
forum: General Help
---

### Post by Hungry Balrog on 2011-05-04
I've been using Ubuntu 10.04 LTS for almost a year now in WUBI with WinXP.  I'm a relative noob with Linux, though always eager to learn more.

Lately, I have noticed that every now and then Ubuntu stops working for about 30 seconds or so with the hard disk light solidly on.  Clicking anywhere does nothing until it wakes up and then remembers all my previous clicks.

When it doesn't do this, it works wonderfully.  I can't figure out what sets it off.  And some days it does it annoyingly often and other days not at all or rarely.

I checked the log files and this is a sample of some troubled times:

```
May  2 19:32:17 ubuntu kernel: [  909.000011] ata1: lost interrupt (Status 0x58)
May  2 19:32:17 ubuntu kernel: [  909.000064] ata1: soft resetting link
May  2 19:32:17 ubuntu kernel: [  909.196337] ata1.00: configured for UDMA/133
May  2 19:32:17 ubuntu kernel: [  909.196342] ata1.00: device reported invalid CHS sector 0
May  2 19:32:17 ubuntu kernel: [  909.196348] ata1: EH complete
May  2 19:32:49 ubuntu kernel: [  941.000018] ata1: lost interrupt (Status 0x58)
May  2 19:32:50 ubuntu kernel: [  941.000079] ata1: soft resetting link
May  2 19:32:50 ubuntu kernel: [  941.180360] ata1.00: configured for UDMA/133
May  2 19:32:50 ubuntu kernel: [  941.180366] ata1.00: device reported invalid CHS sector 0
May  2 19:32:50 ubuntu kernel: [  941.180375] ata1: EH complete
May  2 19:33:00 ubuntu pulseaudio[1292]: ratelimit.c: 383 events suppressed
May  2 19:45:57 ubuntu kernel: [ 1729.000051] ata1: lost interrupt (Status 0x58)
May  2 19:45:57 ubuntu kernel: [ 1729.000111] ata1: soft resetting link
May  2 19:45:57 ubuntu kernel: [ 1729.180408] ata1.00: configured for UDMA/133
May  2 19:45:57 ubuntu kernel: [ 1729.180418] ata1.00: device reported invalid CHS sector 0
May  2 19:45:57 ubuntu kernel: [ 1729.180432] ata1: EH complete
May  2 19:55:06 ubuntu kernel: [ 2278.000045] ata1: lost interrupt (Status 0x58)
May  2 19:55:06 ubuntu kernel: [ 2278.000103] ata1: soft resetting link
May  2 19:55:06 ubuntu kernel: [ 2278.196406] ata1.00: configured for UDMA/133
May  2 19:55:06 ubuntu kernel: [ 2278.196417] ata1.00: device reported invalid CHS sector 0
May  2 19:55:06 ubuntu kernel: [ 2278.196434] ata1: EH complete
May  2 19:55:39 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="764" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.

```The repeating pattern that starts with "lost interrupt" happens every time my computer freezes for a while.  I thought it had something to do with my hard disk.  However, I checked the SMART software and it says my disk is okay.  It has a reallocated sector count of 73 and a current pendins sector count of 1.  Everything else passes as "good."  I have never noticed this kind of hang in Win XP, though I haven't used it very much in the past few months, thanks to Ubuntu.

Here are my hardware specs, in case this turns out to be some known hardware issue:

Processor:AMD Athlon 3200+
Motherboard: NForce4-A939
HD: ATA Hitachi HDS721616PLAT80, a 160GB drive attached by paralell ATA
Video card: GeForce 7800GTX
DVD-RW: Philips DVD8701

The computer is connected to a Lexmark X3350 that only works under Windows.  I frequently connect a flash drive to the machine as well.  

Any suggestions?

---

### Post by majorawesome on 2011-05-04
Maybe you should upgrade to 11.04? A LOT of things have been improved/fixed since 10.04

---

### Post by Hungry Balrog on 2011-05-04
Maybe.  I was thinking of trying to shrink my WinXP partition and giving Linux its own partition.  But I don't want to do that if my hardware is just not going to play nice or if my hard drive (or other hardware component) is failing.  

I am a bit skeptical of the SMART data telling me everything is okay.  I had two hard drives die on me before (one in this machine).  The whole time SMART said everything was okay even though the drive was bad.

---

### Post by Hungry Balrog on 2011-05-14
Fixed.  

The source of the trouble was a bad PATA cable.  I was using two PATA cables - one for the HDD and one for the DVD-RW.  I hooked the two devices together on DVD-RW's cable and the problems went away.

---

