---
title: "Dell Latitude 610 / Broadcom 1370: Wireless access doesn't work"
date: 2006-02-23
forum: General Help
---

### Post by pgoetz on 2006-02-23
Hi -

I am unable to get wireless access working on a Dell Latitude 610 and strongly suspect that it simple does not work with ndiswrapper version 1.1, the one which ships with Breezy.

The Latitude 610 features a Broadcom 1370 wireless chip which uses the windows bcmwl5.inf driver file.  I followed all the instructions given in the " HOW TO: Configure wireless cards with Broadcom chipsets:" [http://www.ubuntuforums.org/showthread.php?t=25683&page=33](http://www.ubuntuforums.org/showthread.php?t=25683&page=33)

Whenever I try to modprobe ndiswrapper, I get the following errors in /var/log/syslog:

Feb 23 15:30:03 localhost kernel: [4306469.660000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
Feb 23 15:30:03 localhost kernel: [4306469.681000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:strrchr
Feb 23 15:30:03 localhost kernel: [4306469.681000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmFreeContiguousMemorySpecifyCache
Feb 23 15:30:03 localhost kernel: [4306469.681000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmAllocateContiguousMemorySpecifyCache
Feb 23 15:30:03 localhost kernel: [4306469.681000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmGetPhysicalAddress
Feb 23 15:30:03 localhost kernel: [4306469.681000] ndiswrapper (load_sys_files:456): unable to prepare driver 'bcmwl5'
Feb 23 15:30:03 localhost kernel: [4306469.700000] ndiswrapper (ndiswrapper_load_driver:92): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'


I strongly suspect that ndiswrapper 1.8 (the one shipping with Dapper) will work, but haven't had a chance to recompile the src package yet to make it work with the Breezy kernel.

Can someone else confirm/deny this?  I'm incredulous that no one else has run into this problem!

---

### Post by spo0ner on 2006-05-04
I also have a Lat 610 and have been unsuccessful in getting the wireless to work.
I couldn't get Dapper to LiveCD install on to my system so I had to install Breezy and then dist-upgrade.
I also had to configure the NTFS mount (dual boot system) manually.

Dapper is nice but it just doesn't seem to be very laptop ready at least as far a my Dell 610 goes.

---

### Post by DavidFourer on 2006-05-12
I also have a dell with broadcom 1370 wireless lan that I can't get to work.  Same problem.  Breezy v5.10 standard install

---

