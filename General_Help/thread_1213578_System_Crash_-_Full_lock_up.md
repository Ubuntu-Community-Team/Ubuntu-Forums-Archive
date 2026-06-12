---
title: "System Crash - Full lock up"
date: 2009-07-15
forum: General Help
---

### Post by ZebCarnell on 2009-07-15
Hi guys
I'm having some issues with my Dell GX60. Every half hour or so the machine locks up (and I mean completely). 
It's possible its a heat issue but there is no way to tell because Dell doesn't seem to worry about CPU heat Sensors (the motherboards don't allow over-clocking). So lm-sensors, etc don't work.

I had changed the default CPU (Celeron 1.8 socket 478 ) to a P4 2.4 socket 478 and since then this has happened, though I did make some other changes at the same time, like adding 256mb's of RAM. The CPU is running under-clocked at the motherboard's default 1.8 (for the celeron). Could this also be a voltage issue?

I've checked thermal paste (reapplied). 


And I've finally got a read out from /var/log/messages :

```
Jul 15 15:35:03 server -- MARK --
Jul 15 15:35:15 server kernel: [ 3629.754514] *pde = 007b7067 *pte = 00000000 
Jul 15 15:35:16 server kernel: [ 3629.754537] Dumping ftrace buffer:
Jul 15 15:35:16 server kernel: [ 3629.754543]    (ftrace buffer empty)
Jul 15 15:35:16 server kernel: [ 3629.754546] Modules linked in: binfmt_misc i91
5 drm bridge stp bnep input_polldev video output lp ppdev dcdbas arc4 ecb rt73us
b crc_itu_t pcspkr iTCO_wdt iTCO_vendor_support rt2500usb rt2x00usb rt2x00lib le
d_class mac80211 shpchp cfg80211 intel_agp agpgart parport_pc parport usbhid e10
0 mii floppy fbcon tileblit font bitblit softcursor
Jul 15 15:35:16 server kernel: [ 3629.754588] 
Jul 15 15:35:16 server kernel: [ 3629.754594] Pid: 2650, comm: Xorg Not tainted 
(2.6.28-13-generic #45-Ubuntu) OptiPlex GX60                
Jul 15 15:35:16 server kernel: [ 3629.754599] EIP: 0060:[<ed924cc0>] EFLAGS: 002
13282 CPU: 0
Jul 15 15:35:16 server kernel: [ 3629.754605] EIP is at 0xed924cc0
Jul 15 15:35:16 server kernel: [ 3629.754609] EAX: fffffff2 EBX: 00000000 ECX: 0
0000008 EDX: fffffff2
Jul 15 15:35:16 server kernel: [ 3629.754614] ESI: edbebee4 EDI: c02cd7a6 EBP: 0
0000001 ESP: edbebedc
Jul 15 15:35:16 server kernel: [ 3629.754618]  DS: 007b ES: 007b FS: 00d8 GS: 00
33 SS: 0068
Jul 15 15:35:16 server kernel: [ 3629.754629]  e33ee200 ee7b2000 ed799528 ee7b20
18 e3225a80 d6bd99a0 ed799708 edbebf1c
Jul 15 15:35:16 server kernel: [ 3629.754809] ---[ end trace 2c466192c449fda0 ]-
--

```

Could someone please look through that and see if they can supply me with any more information?

Also before you suggest, I'm running mem-test now ;)


Any help would be hugely appreciated.
Cheers,
Zeb

---

### Post by ZebCarnell on 2009-07-15
After looking through the messages log, I can see that the log above isn't accurate. This is more like what it shows. These are usually after a blank period in the log or a "server -- MARK --" until I pull the power:

```
Jul 14 18:03:02 server syslogd 1.5.0#5ubuntu3: restart.
Jul 14 18:29:14 server syslogd 1.5.0#5ubuntu3: restart.
Jul 14 18:29:16 server syslogd 1.5.0#5ubuntu3: restart.
Jul 13 18:57:46 server syslogd 1.5.0#5ubuntu3: restart.
Jul 13 19:22:38 server syslogd 1.5.0#5ubuntu3: restart.
Jul 13 19:32:53 server syslogd 1.5.0#5ubuntu3: restart.
Jul 14 07:59:34 server syslogd 1.5.0#5ubuntu3: restart.
Jul 14 09:37:08 server syslogd 1.5.0#5ubuntu3: restart.
Jul 14 11:19:29 server syslogd 1.5.0#5ubuntu3: restart.
Jul 14 16:13:38 server syslogd 1.5.0#5ubuntu3: restart.
Jul 14 16:37:26 server syslogd 1.5.0#5ubuntu3: restart.
Jul 14 20:06:00 server syslogd 1.5.0#5ubuntu3: restart.
Jul 14 23:43:03 server syslogd 1.5.0#5ubuntu3: restart.
Jul 14 23:45:13 server syslogd 1.5.0#5ubuntu3: restart.
Jul 14 23:48:00 server syslogd 1.5.0#5ubuntu3: restart.
Jul 15 07:55:31 server syslogd 1.5.0#5ubuntu3: restart.
Jul 15 09:53:35 server syslogd 1.5.0#5ubuntu3: restart.
Jul 15 10:23:55 server syslogd 1.5.0#5ubuntu3: restart.
Jul 15 10:48:37 server syslogd 1.5.0#5ubuntu3: restart.
Jul 15 10:58:57 server syslogd 1.5.0#5ubuntu3: restart.
Jul 15 12:10:26 server syslogd 1.5.0#5ubuntu3: restart.
Jul 15 12:14:37 server syslogd 1.5.0#5ubuntu3: restart.
Jul 15 12:18:49 server syslogd 1.5.0#5ubuntu3: restart.
Jul 15 12:26:29 server syslogd 1.5.0#5ubuntu3: restart.
Jul 15 14:35:12 server syslogd 1.5.0#5ubuntu3: restart.
Jul 15 15:53:20 server syslogd 1.5.0#5ubuntu3: restart.

```

CPU Heat? Looks like the hardware is doing it, if the OS has no logs showing info.

---

