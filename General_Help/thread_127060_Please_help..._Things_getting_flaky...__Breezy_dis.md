---
title: "Please help... Things getting flaky...  Breezy disintegrating"
date: 2006-02-08
forum: General Help
---

### Post by stardotstar on 2006-02-08
After many months of getting Ubuntu more and more finely tuned (running Breezy for the last couple - and indeed only freshly installed since a few weeks ago due to some networking issues) I have had an almost dream run.

I have not experienced any real show stoppers till just now.  Everything I have needed to fix I have found ready support for and almost everything that has gone strange has been fixed with the right configuration, packages etc...

But just now things have started to deteriorate.

First sign was CUPS going awol (FF decided to hang when trying to print so I began to investigate) - I had set up two LPR printers that were printing perfectly via the wifi and wired LAN.  Now the gnome cups manager says Starting Printing but that disappears and nothing ever happens except if I leave the machine for long enough a nameless "error" window without buttons or content - which I assume it associated with CUPS timing out.  (I have since started and restarted, reinstalled (complete removal) cups, gnome cups etc etc)

Then the name service began hanging on shutdown so I removed BIND (didn't need it - never specifically chose to add it but then again never had any issues with it before).

Then the gnome panels started initialising but never finishing loading their content - couldn't left click or do anything - save switch to a terminal killall gnome-panel and switch back which often worked.

Then quite by chance (while doing things like testing the older kernel (no different) I found that launching the date and time settings system panel brings up an empty window - just the white holes where content should be - no buttons or text at all.  It has to be force quit!

Trying to see if other services were a problem I launched the services manager - it takes several minutes to come up.  Also the Disks Manager takes several minutes of no apparent activity to appear.

I am using Firefox 1.5 and Thunderbird, Open Office seems to work and networking is basically OK except I had to switch off Network Manager because it was competintg with the gnome manager I think.

Kernels are 2.6.12-10 and 2.6.12-9 both do the same things.

The box is an IBM Thinkpad R51

I am at a loss .

Can I get some ideas on what to do - if I have to rebuild the system that is ok but I will need help ensuring I don't lose my home profile and files.  I have mainly only installed synaptic ubuntu repository software so I can make the effort to rebuild but I would rather work out the problem.

This is the first time that my experience has made me think about those "not ready for the desktop" threads which I hardly read because Ubuntu has so far been awesome.

Guidance needed, patience sought and expertise sincerely appreciated...

I know a quick check of my posts will show these things starting to happen just recently and that in the past I have tended to meddle a bit - but I can assure you that the system should not be in a bad state - it really just seems to have started to deteriorate out of the blue.

Will

```

wparker@geko:~$ tail -100  /var/log/syslog
Feb  8 20:39:23 localhost kernel: [4294699.844000] shpchp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
Feb  8 20:39:23 localhost kernel: [4294699.844000] shpchp: acpi_shpchprm:   Slot sun(2) at s:b:d:f=0x00:02:00:01
Feb  8 20:39:23 localhost kernel: [4294699.848000] shpchp: shpc_init : shpc_cap_offset == 0
Feb  8 20:39:23 localhost kernel: [4294699.848000] shpchp: shpc_init : shpc_cap_offset == 0
Feb  8 20:39:23 localhost kernel: [4294699.848000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb  8 20:39:23 localhost kernel: [4294700.073000] hw_random hardware driver 1.0.0 loaded
Feb  8 20:39:23 localhost kernel: [4294700.215000] tpm_atmel 0000:00:1f.0: Atmel TPM version 1.1.0.6
Feb  8 20:39:23 localhost kernel: [4294700.421000] ACPI: PCI Interrupt 0000:00:1f.5[b] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Feb  8 20:39:23 localhost kernel: [4294700.421000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Feb  8 20:39:23 localhost kernel: [4294701.231000] intel8x0_measure_ac97_clock: measured 49452 usecs
Feb  8 20:39:23 localhost kernel: [4294701.231000] intel8x0: clocking to 48000
Feb  8 20:39:23 localhost kernel: [4294701.599000] Linux Kernel Card Services
Feb  8 20:39:23 localhost kernel: [4294701.599000]   options:  [pci] [cardbus] [pm]
Feb  8 20:39:23 localhost kernel: [4294701.608000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb  8 20:39:23 localhost kernel: [4294701.608000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
Feb  8 20:39:23 localhost kernel: [4294701.608000] Yenta: Using INTVAL to route CSC interrupts to PCI
Feb  8 20:39:23 localhost kernel: [4294701.608000] Yenta: Routing CardBus interrupts to PCI
Feb  8 20:39:23 localhost kernel: [4294701.608000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
Feb  8 20:39:23 localhost kernel: [4294701.829000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
Feb  8 20:39:23 localhost kernel: [4294701.829000] Socket status: 30000086
Feb  8 20:39:23 localhost kernel: [4294701.929000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
Feb  8 20:39:23 localhost kernel: [4294701.929000] ACPI: PCI Interrupt 0000:02:00.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Feb  8 20:39:23 localhost kernel: [4294701.982000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c0215000-c02157ff]  Max Packet=[2048]
Feb  8 20:39:23 localhost kernel: [4294702.103000] ieee80211_crypt: registered algorithm 'NULL'
Feb  8 20:39:23 localhost kernel: [4294702.106000] ieee80211: 802.11 data/management/control stack, 1.0.3
Feb  8 20:39:23 localhost kernel: [4294702.106000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Feb  8 20:39:23 localhost kernel: [4294702.113000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
Feb  8 20:39:23 localhost kernel: [4294702.113000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
Feb  8 20:39:23 localhost kernel: [4294702.116000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Feb  8 20:39:23 localhost kernel: [4294702.116000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Feb  8 20:39:23 localhost kernel: [4294703.239000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00061b03240241b5]
Feb  8 20:39:23 localhost kernel: [4294703.974000] input: PC Speaker
Feb  8 20:39:23 localhost kernel: [4294704.026000] Real Time Clock Driver v1.12
Feb  8 20:39:23 localhost kernel: [4294704.113000] Floppy drive(s): fd0 is 1.44M
Feb  8 20:39:23 localhost kernel: [4294704.127000] FDC 0 is a National Semiconductor PC87306
Feb  8 20:39:23 localhost kernel: [4294704.217000] irda_init()
Feb  8 20:39:23 localhost kernel: [4294704.217000] NET: Registered protocol family 23
Feb  8 20:39:23 localhost kernel: [4294707.656000] ACPI: AC Adapter [AC] (on-line)
Feb  8 20:39:23 localhost kernel: [4294707.769000] ACPI: Battery Slot [BAT0] (battery present)
Feb  8 20:39:23 localhost kernel: [4294707.786000] ACPI: Power Button (FF) [PWRF]
Feb  8 20:39:23 localhost kernel: [4294707.786000] ACPI: Lid Switch [LID]
Feb  8 20:39:23 localhost kernel: [4294707.786000] ACPI: Sleep Button (CM) [SLPB]
Feb  8 20:39:23 localhost kernel: [4294707.877000] ibm_acpi: IBM ThinkPad ACPI Extras v0.8
Feb  8 20:39:23 localhost kernel: [4294707.877000] ibm_acpi: http://ibm-acpi.sf.net/
Feb  8 20:39:23 localhost kernel: [4294707.878000] ibm_acpi: dock device not present
Feb  8 20:39:23 localhost kernel: [4294707.985000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Feb  8 20:39:30 localhost cardmgr[7889]: watching 1 socket
Feb  8 20:39:30 localhost kernel: [4294716.776000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
Feb  8 20:39:30 localhost kernel: [4294716.777000] cs: IO port probe 0xc00-0xcf7: clean.
Feb  8 20:39:30 localhost kernel: [4294716.778000] cs: IO port probe 0xa00-0xaff: clean.
Feb  8 20:39:30 localhost cardmgr[7894]: starting, version is 3.2.5
Feb  8 20:39:31 localhost /usr/sbin/cron[8018]: (CRON) INFO (pidfile fd = 3)
Feb  8 20:39:31 localhost /usr/sbin/cron[8019]: (CRON) STARTUP (fork ok)
Feb  8 20:39:32 localhost /usr/sbin/cron[8019]: (CRON) INFO (Running @reboot jobs)
Feb  8 20:39:32 localhost kernel: [4294718.846000] [drm] Initialized drm 1.0.0 20040925
Feb  8 20:39:32 localhost kernel: [4294718.849000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb  8 20:39:32 localhost kernel: [4294718.851000] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
Feb  8 20:39:32 localhost kernel: [4294718.852000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Feb  8 20:39:32 localhost kernel: [4294718.852000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Feb  8 20:39:32 localhost kernel: [4294718.852000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Feb  8 20:48:04 localhost gconfd (wparker-8155): starting (version 2.12.0), pid 8155 user 'wparker'
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readwrite:/home/wparker/.gconf" to a writable configuration source at position 2
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Feb  8 20:48:05 localhost kernel: [4295232.051000] NET: Registered protocol family 10
Feb  8 20:48:05 localhost kernel: [4295232.051000] Disabled Privacy Extensions on device c02eb280(lo)
Feb  8 20:48:05 localhost kernel: [4295232.051000] IPv6 over IPv4 tunneling driver
Feb  8 20:48:21 localhost gconfd (wparker-8155): Resolved address "xml:readwrite:/home/wparker/.gconf" to a writable configuration source at position 0
Feb  8 20:49:00 localhost gconfd (root-8295): starting (version 2.12.0), pid 8295 user 'root'
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Feb  8 20:49:12 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Feb  8 20:49:12 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Feb  8 20:49:12 localhost dhclient: All rights reserved.
Feb  8 20:49:12 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
Feb  8 20:49:12 localhost dhclient:
Feb  8 20:49:12 localhost dhclient: sit0: unknown hardware address type 776
Feb  8 20:49:12 localhost dhclient: sit0: unknown hardware address type 776
Feb  8 20:49:12 localhost kernel: [4295299.180000] NET: Registered protocol family 17
Feb  8 20:49:12 localhost dhclient: Listening on LPF/eth1/00:12:f0:35:4e:7e
Feb  8 20:49:12 localhost dhclient: Sending on   LPF/eth1/00:12:f0:35:4e:7e
Feb  8 20:49:12 localhost dhclient: Sending on   Socket/fallback
Feb  8 20:49:13 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Feb  8 20:49:13 localhost dhclient: DHCPACK from 192.168.0.1
Feb  8 20:49:13 localhost dhclient: bound to 192.168.0.103 -- renewal in 239084 seconds.
Feb  8 20:49:22 localhost kernel: [4295309.363000] eth1: no IPv6 routers present
Feb  8 20:49:30 localhost gconfd (root-8295): GConf server is not in use, shutting down.
Feb  8 20:49:30 localhost gconfd (root-8295): Exiting
Feb  8 20:49:42 localhost kernel: [4295328.646000] ipw2200: Firmware error detected.  Restarting.

``` messages is much the same
```

Feb  8 20:39:32 localhost kernel: [4294718.852000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Feb  8 20:39:32 localhost kernel: [4294718.852000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Feb  8 20:39:32 localhost kernel: [4294718.852000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Feb  8 20:48:04 localhost gconfd (wparker-8155): starting (version 2.12.0), pid 8155 user 'wparker'
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readwrite:/home/wparker/.gconf" to a writable configuration source at position 2
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Feb  8 20:48:05 localhost gconfd (wparker-8155): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Feb  8 20:48:05 localhost kernel: [4295232.051000] NET: Registered protocol family 10
Feb  8 20:48:05 localhost kernel: [4295232.051000] Disabled Privacy Extensions on device c02eb280(lo)
Feb  8 20:48:05 localhost kernel: [4295232.051000] IPv6 over IPv4 tunneling driver
Feb  8 20:48:21 localhost gconfd (wparker-8155): Resolved address "xml:readwrite:/home/wparker/.gconf" to a writable configuration source at position 0
Feb  8 20:49:00 localhost gconfd (root-8295): starting (version 2.12.0), pid 8295 user 'root'
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Feb  8 20:49:00 localhost gconfd (root-8295): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Feb  8 20:49:12 localhost kernel: [4295299.180000] NET: Registered protocol family 17
Feb  8 20:49:30 localhost gconfd (root-8295): GConf server is not in use, shutting down.
Feb  8 20:49:30 localhost gconfd (root-8295): Exiting

```

---

### Post by stardotstar on 2006-02-08
Further to this the system seems to be working - I got into work after having it on all night without any errors etc.  Firefox is working the panels are ok but all the service control panels are taking heaps of time to launch.  Is there a test I can do to work out what might be resource hogging or causing slow system control performance...  Most system processes are sleeping and cpu and memory and disk utilisation are minimal in the system monitor.  Apps like FF start up quickly, the networking is working but it is still not quite right.

Will

---

### Post by dcstar on 2006-02-08
[QUOTE=stardotstar]Further to this the system seems to be working - I got into work after having it on all night without any errors etc.  Firefox is working the panels are ok but all the service control panels are taking heaps of time to launch.  Is there a test I can do to work out what might be resource hogging or causing slow system control performance... Apps like FF start up quickly, the networking is working but it is still not quite right.

Will[/QUOTE]
I notice you seem to be using IPv6, this has been an issue for a lot of people so you may want to turn it off.

Do a forum search for "IPv6 disable" and you should see the many posts on how to do this.

---

### Post by stardotstar on 2006-02-09
Thanks for the thought David, that had never crossed my mind.  I have disabled it as suggested but the problems persist.

gnome-panel problems, slow system config apps, broken date and time control panel.

edit - after leaving the date and time for a while it came good - just like the disk manager, and services - just reallllllllly slooooooooooow...  unbelievable compared to how it used to run.

---

### Post by arphe_el on 2006-02-09
take time to back-up your files before it's too late. from my point of view and based from my experience an installation via CD is much more effective than update using synaptic or apt-get.

hope this helps you. GODspeed! :)

---

### Post by Mustard on 2006-02-09
Its probably not something you want to hear, but its quite possible...you could be experiencing the symptoms of an approaching hardware failure.  Its possible your disk drive is about to die or that some type of file corruption has or could take place.  As suggested above, it might be best to abandon ship now and get your important files off the hard drive.  I'd try running some checks on your disk drive to see if its detecting any bad blocks.

-edit-

I've dug up this link for you on a method of backing up your filesystem using the tarball method.

[http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)

Alternatively, you could just tarball your $HOME directory.

---

### Post by stardotstar on 2006-02-09
Thanks Mustard, I am making a backup right now and will burn it asap.

I will also do a backup of my other partitions very soon since I have my Work XP partition on this disk too.  

Funnily enough I find that when the network is not activated the system performance is better - the time and date came straight up then and not now - that I am connected wirelessly and in FF typing this.  The Cups error can be taking up to 5minutes to pop up and services while it started immediately when I first booted and was not connected is now taking many minutes to come up.

Here's hoping 1) it is nothing too serious - 2) that it is something that means it is not some Breezy configuration issue I have somehow contribnuted to without knowing or knowing how to troubleshoot.

Will

---

### Post by Mustard on 2006-02-09
[QUOTE=stardotstar]Thanks Mustard, I am making a backup right now and will burn it asap.

I will also do a backup of my other partitions very soon since I have my Work XP partition on this disk too.  

Funnily enough I find that when the network is not activated the system performance is better - the time and date came straight up then and not now - that I am connected wirelessly and in FF typing this.  The Cups error can be taking up to 5minutes to pop up and services while it started immediately when I first booted and was not connected is now taking many minutes to come up.

Here's hoping 1) it is nothing too serious - 2) that it is something that means it is not some Breezy configuration issue I have somehow contribnuted to without knowing or knowing how to troubleshoot.

Will[/QUOTE]

Hmmm..ok.  Its still worth making backups, because its doesnt sound like a good situation.  The fact that it seems to be only happening when your network is active might be move suspicion away from your hard drive.  I'd investigate that angle anyway, because slowness in the system is definitely a symptom of a potential hardware failure.  Correcting itself with network disabled does seem to point the finger directly at networking though.

The only error message I could see in your above posts that really looked like a clue to me, was the 'Error in firmware' at the end. Anyway if its a networking problem I'm probably going to be more bothersome than a help.  I'm hopeless with networking. :)

---

### Post by stardotstar on 2006-02-09
Thanks again for a speedy and thoughtful reply.  

It does look like network but then again I have just pushed 2.1 G across my 54mb wireless connection via the card that the firmware error relates to and during this time FF has been working just fine, the tar and copying via galeon and the shell/terminal all worked faultlesly but the system control panels remain in a state of disrepair - slow, slow slow 

I would like to home in on what is causing this because my other option is to blow the system away and use my just downloaded full iso of Breezy 5.10...

I will have to research restoring my home environment though because I have put a lot of work into building it.  But then again that may copy a flaw straight back into the new distro!! :ohho:

Anyway I'll keep investigating and in the mean time do a full back of my XP part and even consider doing a complete system rebuild swapping the disk allocation from 30GB XP/10GB Ubuntu to 30GB Ubuntu/10GB XP (if the bloatware will fit in that which I doubt!)

What other syslog/messages should I be focusing on??


edit : something I just noticed - I went to shut down my network connection to see if things came back to normal.  So I launched the network connection manager via the monitor applet (still waiting for it to come up several minutes now)

in the mean time I thought I'd try to down the adapter with ifdown.  Wierd things happening - appeared to be no loopback - and although eth1 is clearly working wirelessly for internet and lan, there is something wrong with the interfaces file cause I couldn't access it with ifdown (unless the starting network control panel had locked it)

any ideas from this session at the shell:

```

wparker@geko:~$ sudo ifdown eth0
Password:
/etc/network/interfaces:27: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
wparker@geko:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:12:F0:35:4E:7E
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe35:4e7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:931534 errors:1 dropped:1 overruns:0 frame:0
          TX packets:1391751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:91757398 (87.5 MiB)  TX bytes:2011481725 (1.8 GiB)
          Interrupt:11 Base address:0x6000 Memory:c0214000-c0214fff

wparker@geko:~$ sudo ifdown eth1
/etc/network/interfaces:27: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
wparker@geko:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface




iface eth0 inet dhcp



iface eth1 inet dhcp
wireless-essid skink
wireless-key s:******

iface eth1 inet dhcp
wireless-essid skink
wireless-key s:******


auto lo



auto eth1

``` 
Will

edit: just confirming - it looks like networking, once the network control panel came up I killed the interface and things in the system control panel started working fast:

time and date came straight up, disks launched straight away, network manager came up immediately - I was able to reconnect and post this.

and things are slooooooow again...  But internet browsing and most application things seem totally unaffected - not sure if this points to a wierd local network resolution thing to do with the hostname, loopback or something.....

---

### Post by Ocxic on 2006-02-09
i know this may sound silly, but is it possible you may have contracted some type of virus. i know there super rare, if non-exsitant but this irratic behavoir seems like something a virus could cause. could you run a virus check just for the hell of it?

---

### Post by Mustard on 2006-02-09
I've edited my above post a bit, because I was floundering in the dark a bit there, not really having much experience with networking.

For troubleshooting, all your logs are in /var/log/. 

Xorg.0.log relates to xorg so I'm not that sure whether you will find anything in there, but you could have a look.

You might try this command in terminal too...

```
dmesg | tail 
```

This should print out the last section of dmesg and you might spot something that might seem to relate to the problem.

Is cpu usage high?  What does the 'top' command show in terminal with regards to what percentage of  cpu some processes are using?

---

### Post by Mustard on 2006-02-09
Just reading your edit.... local interface and loopback..hmmm..reminds me of a thread I just read....I'll be back with a link...

-edit-

Hmmm..cant find the thread now.

Whats the contents of your /etc/network/interfaces file?


Oh..and one more file...whats the contents of your /etc/hosts file?

---

### Post by stardotstar on 2006-02-09
OK I twigged that since it looked like networking but the internet and LAN worked it could be a local host problem.

Suddenly it was obvious - anything trying to lookup the local host was timing out (read hanging) becasue lo had gone.

How I don't know.

Check it out:

```

wparker@geko:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:25:86:38:74
          inet addr:172.27.14.6  Bcast:172.27.14.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe86:3874/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5534576 (5.2 MiB)  TX bytes:824613 (805.2 KiB)
          Base address:0x8000 Memory:c0220000-c0240000

wparker@geko:~$ sudo ifup eth1
Password:
/etc/network/interfaces:22: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"
wparker@geko:~$ sudo ifup lo
Password:
/etc/network/interfaces:22: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"
wparker@geko:~$

wparker@geko:/etc/init.d$ sudo ifconfig lo up
Password:
wparker@geko:/etc/init.d$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:25:86:38:74
          inet addr:172.27.14.6  Bcast:172.27.14.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe86:3874/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7866452 (7.5 MiB)  TX bytes:1410795 (1.3 MiB)
          Base address:0x8000 Memory:c0220000-c0240000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wparker@geko:/etc/init.d$

``` 
and suddenly all is well again - how could this happen?  why did loopback disappear and then not come back with subsequent reboots... How do I fix it and make sure it never happens again?

Thanks for all the patience and assistance in getting to the bottom of this.  It seems all too simple but makes sense - I just don't know what brought it on!

```

wparker@geko:~$ cat /etc/hosts
127.0.0.1 localhost.localdomain localhost geko
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
wparker@geko:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface

iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid skink
wireless-key s:*****

iface eth1 inet dhcp
wireless-essid skink
wireless-key s:*****
auto lo



auto eth0
wparker@geko:~$

```

---

### Post by Mustard on 2006-02-09
I'm not sure why it would go down.  I was reading about a similar problem in another thread.  I believe that was unresolved too.  Its good news that you have at least isolated the problem though. :)

---

### Post by stardotstar on 2006-02-09
How about this:

What would having the auto lo in the /etc/network/interfaces file do?

I removed the second auto lo and found that ifup and down can be called from the shell now - those errors about not being able to read it have gone.

I thought the control panel program rewrote this file every time anyway so why would there be any bad code in there?

```

wparker@geko:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface

iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid Casper
wireless-key s:*****


auto eth0
``` 
Here's hoping I'm onto something.,..

---

