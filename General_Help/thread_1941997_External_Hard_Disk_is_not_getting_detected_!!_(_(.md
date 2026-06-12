---
title: "External Hard Disk is not getting detected !! :( :("
date: 2012-03-16
forum: General Help
---

### Post by harivittal.hk on 2012-03-16
Hi All,

My Seagate Go Flex External Hard Disk is not getting detected . Am using dual OS viz Linux n Win XP !

Can some one help me in troubleshooting this !

Thanks in Advance.

Regards,
Hari V

---

### Post by zero2xiii on 2012-03-16
And I would LOVE a marshmellow factory on a hill with a view...

Seriously? What is the DETAILS of your problem.

But im still going to help you (on the same note as your post):


**Your controler is broken, go buy a new one** ):P

Please supply MUCH more details regarding your problem and MAYBE we can help you.

Cherz

---

### Post by piratebill on 2012-03-16
> **zero2xiii said:**
> And I would LOVE a marshmellow factory on a hill with a view...

Seriously? What is the DETAILS of your problem.

But im still going to help you (on the same note as your post):


**Your controler is broken, go buy a new one** ):P

Please supply MUCH more details regarding your problem and MAYBE we can help you.

Cherz


While I agree the more details the better, there is a thing called tact.

Anyways, with the drive plugged in, what are the results of 
```
sudo fdisk -l
```

and 

```
lsusb
```

---

### Post by zero2xiii on 2012-03-16
> **piratebill said:**
> While I agree the more details the better, there is a thing called tact.



Agreed, I apologize. But he could atleast mention whether or not it gives the same issue under windows AND linux for example, not just "It doesn't get detected" this can mean so many different things. (But I know I dont have to explain)

So again, I am sorry for my harsh response. We really need a sticky thread with scripts for these common fault finding techniques, so that this step can be avoided. And we can get the inforation we need in the FIRST POST.

Cherz

---

### Post by harivittal.hk on 2012-03-16
hi ,

thanks for those remarks , am really happy that you came up to help on this..
btw sudo fdisk -l shows :
 [B][COLOR="Red"]
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea530

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6247    50178996    7  HPFS/NTFS
/dev/sda2            6248       19458   106110990    f  W95 Ext'd (LBA)
/dev/sda5            6248       10709    35840983+   7  HPFS/NTFS
/dev/sda6           10710       15879    41527993+   7  HPFS/NTFS
/dev/sda7           15880       18850    23859200   83  Linux
/dev/sda8           18850       19458     4881408   82  Linux swap / Solaris
.[/COLOR][/COLOR][/B]
In winxp too i have faced similar problems, i did troubleshooting work by uninstalling the USB Root HUB in Device Manager, but no much luck !!

Awaiting response on this.

thank you.

---

### Post by piratebill on 2012-03-16
> **zero2xiii said:**
> Agreed, I apologize. But he could atleast mention whether or not it gives the same issue under windows AND linux for example, not just "It doesn't get detected" this can mean so many different things. (But I know I dont have to explain)

So again, I am sorry for my harsh response. We really need a sticky thread with scripts for these common fault finding techniques, so that this step can be avoided. And we can get the inforation we need in the FIRST POST.

Cherz

No worries dude! :)

As for the drive, something is very amiss.  Your system isn't seeing it at all.  What is the output of lsusb?

---

### Post by codemaniac on 2012-03-16
Shows one hdd is attached to your system .I guess it is the internal one .
Please post the output of the below one also
```
lsusb
```

---

### Post by harivittal.hk on 2012-03-16
Hello ,

Out put of lsusb :

[B][COLOR="Red"]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bc2:5020 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR][/B]

Thanks again for contd assistance !! Cheers !! :)

---

### Post by piratebill on 2012-03-16
Ok, your computer does see the external encloser.  strange it doesn't see it as a drive though (something is very wrong).  what is the output of dmesg if you unplug the drive, and plug it back in?

---

### Post by Rebelli0us on 2012-03-16
Are you plugging into a USB3 port? Your hardware might be incompatible.

---

### Post by piratebill on 2012-03-16
> **Rebelli0us said:**
> Are you plugging into a USB3 port? Your hardware might be incompatible.

USB3 is backwards compatible.  Shouldn't be an issue

---

### Post by harivittal.hk on 2012-03-16
Output of DMESG after plugout and plug in 

[COLOR="Red"][B][10451.021382] end_request: I/O error, dev sdb, sector 0
[10451.021392] Buffer I/O error on device sdb, logical block 0
[10451.021402] Buffer I/O error on device sdb, logical block 1
[10451.181320] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10451.181335] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10451.181349] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10451.181361] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[10451.181391] end_request: I/O error, dev sdb, sector 0
[10451.320878] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10451.320887] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10451.320894] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10451.320901] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 01 00 00 07 00
[10451.320920] end_request: I/O error, dev sdb, sector 1
[10451.460181] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10451.460191] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10451.460198] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10451.460205] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10451.460219] end_request: I/O error, dev sdb, sector 0
[10451.621290] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10451.621299] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10451.621307] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10451.621313] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10451.621328] end_request: I/O error, dev sdb, sector 0
[10451.781240] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10451.781248] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10451.781263] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10451.781269] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[10451.781299] end_request: I/O error, dev sdb, sector 56
[10451.901286] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10451.901293] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10451.901298] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10451.901302] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10451.901311] end_request: I/O error, dev sdb, sector 0
[10452.041318] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10452.041332] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10452.041347] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10452.041358] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10452.041390] end_request: I/O error, dev sdb, sector 0
[10452.221306] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10452.221320] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10452.221335] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10452.221351] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff 00 00 00 08 00
[10452.221371] end_request: I/O error, dev sdb, sector 4294967040
[10452.361318] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10452.361333] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10452.361347] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10452.361359] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff e8 00 00 08 00
[10452.361389] end_request: I/O error, dev sdb, sector 4294967272
[10452.541289] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10452.541306] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10452.541321] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10452.541332] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[10452.541362] end_request: I/O error, dev sdb, sector 0
[10452.701456] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10452.701470] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10452.701485] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10452.701497] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 02 00 00 06 00
[10452.701527] end_request: I/O error, dev sdb, sector 2
[10452.861304] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10452.861318] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10452.861333] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10452.861350] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[10452.861370] end_request: I/O error, dev sdb, sector 8
[10453.061289] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10453.061306] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10453.061318] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10453.061330] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff f8 00 00 01 00
[10453.061360] end_request: I/O error, dev sdb, sector 4294967288
[10453.221285] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10453.221294] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10453.221311] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10453.221323] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff f8 00 00 01 00
[10453.221354] end_request: I/O error, dev sdb, sector 4294967288
[10453.421292] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10453.421309] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10453.421322] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10453.421334] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff f8 00 00 01 00
[10453.421363] end_request: I/O error, dev sdb, sector 4294967288
[10453.601283] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10453.601291] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10453.601303] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10453.601314] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff fa 00 00 01 00
[10453.601344] end_request: I/O error, dev sdb, sector 4294967290
[10453.821289] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10453.821298] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10453.821313] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10453.821324] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff f8 00 00 01 00
[10453.821355] end_request: I/O error, dev sdb, sector 4294967288
[10454.021289] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10454.021298] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10454.021313] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10454.021325] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff f8 00 00 01 00
[10454.021356] end_request: I/O error, dev sdb, sector 4294967288
[10454.221297] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10454.221313] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10454.221327] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10454.221339] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff fa 00 00 01 00
[10454.221369] end_request: I/O error, dev sdb, sector 4294967290
[10454.421287] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10454.421296] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10454.421304] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10454.421318] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff f8 00 00 01 00
[10454.421348] end_request: I/O error, dev sdb, sector 4294967288
[10454.601288] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10454.601296] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10454.601304] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10454.601318] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff c0 00 00 08 00
[10454.601348] end_request: I/O error, dev sdb, sector 4294967232
[10454.821298] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10454.821307] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10454.821326] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10454.821338] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff f0 00 00 07 00
[10454.821364] end_request: I/O error, dev sdb, sector 4294967280
[10455.021311] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10455.021330] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10455.021350] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10455.021359] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[10455.021382] end_request: I/O error, dev sdb, sector 8
[10455.220036] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10455.220045] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10455.220053] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10455.220059] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[10455.220088] end_request: I/O error, dev sdb, sector 8
[10455.460225] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10455.460232] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10455.460238] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10455.460243] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff f8 00 00 01 00
[10455.460254] end_request: I/O error, dev sdb, sector 4294967288
[10455.701286] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10455.701295] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10455.701303] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10455.701309] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff f8 00 00 01 00
[10455.701334] end_request: I/O error, dev sdb, sector 4294967288
[10455.901298] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10455.901307] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10455.901314] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10455.901327] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 ff ff ff f0 00 00 07 00
[10455.901357] end_request: I/O error, dev sdb, sector 4294967280
[10455.901366] quiet_error: 174 callbacks suppressed
[10455.901373] Buffer I/O error on device sdb, logical block 4294967280
[10455.901385] Buffer I/O error on device sdb, logical block 4294967281
[10455.901393] Buffer I/O error on device sdb, logical block 4294967282
[10455.901400] Buffer I/O error on device sdb, logical block 4294967283
[10455.901407] Buffer I/O error on device sdb, logical block 4294967284
[10455.901414] Buffer I/O error on device sdb, logical block 4294967285
[10455.901422] Buffer I/O error on device sdb, logical block 4294967286
[10455.901429] Buffer I/O error on device sdb, logical block 4294967287
[10456.141280] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10456.141289] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10456.141296] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10456.141303] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10456.141317] end_request: I/O error, dev sdb, sector 0
[10456.141323] Buffer I/O error on device sdb, logical block 0
[10456.141330] Buffer I/O error on device sdb, logical block 1
[10456.381297] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10456.381306] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10456.381313] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10456.381319] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10456.381354] end_request: I/O error, dev sdb, sector 0
[10456.541296] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10456.541305] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10456.541312] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10456.541318] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10456.541344] end_request: I/O error, dev sdb, sector 0
[10456.721292] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10456.721301] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10456.721309] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10456.721315] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[10456.721335] end_request: I/O error, dev sdb, sector 0
[10456.941308] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10456.941317] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10456.941323] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10456.941328] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 02 00 00 06 00
[10456.941359] end_request: I/O error, dev sdb, sector 2
[10457.141301] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10457.141310] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10457.141317] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10457.141324] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10457.141350] end_request: I/O error, dev sdb, sector 0
[10457.381290] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10457.381299] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10457.381306] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10457.381313] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[10457.381327] end_request: I/O error, dev sdb, sector 0
[10457.500043] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10457.500053] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10457.500060] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10457.500067] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 01 00 00 07 00
[10457.500081] end_request: I/O error, dev sdb, sector 1
[10457.740055] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10457.740062] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10457.740068] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10457.740073] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10457.740084] end_request: I/O error, dev sdb, sector 0
[10457.860906] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10457.860915] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10457.860923] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10457.860929] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 00 00 00 08 00
[10457.860943] end_request: I/O error, dev sdb, sector 2048
[10457.981289] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10457.981298] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10457.981305] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10457.981311] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10457.981325] end_request: I/O error, dev sdb, sector 0
[10458.121285] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10458.121294] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10458.121302] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10458.121308] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[10458.121322] end_request: I/O error, dev sdb, sector 0
[10458.361288] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10458.361297] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10458.361304] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10458.361311] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 01 00 00 07 00
[10458.361325] end_request: I/O error, dev sdb, sector 1
[10458.481300] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10458.481308] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10458.481316] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10458.481322] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10458.481336] end_request: I/O error, dev sdb, sector 0
[10458.601285] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10458.601294] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10458.601301] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10458.601308] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[10458.601321] end_request: I/O error, dev sdb, sector 0
[10458.841287] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10458.841296] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10458.841303] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10458.841309] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 02 00 00 06 00
[10458.841323] end_request: I/O error, dev sdb, sector 2
[10459.041303] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10459.041312] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10459.041319] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10459.041326] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10459.041340] end_request: I/O error, dev sdb, sector 0
[10459.161267] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10459.161277] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10459.161284] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10459.161291] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[10459.161305] end_request: I/O error, dev sdb, sector 0
[10459.401282] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10459.401291] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10459.401298] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10459.401305] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 02 00 00 06 00
[10459.401319] end_request: I/O error, dev sdb, sector 2
[10459.561297] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10459.561307] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10459.561314] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10459.561320] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10459.561334] end_request: I/O error, dev sdb, sector 0
[10459.721281] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10459.721290] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10459.721298] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10459.721304] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[10459.721318] end_request: I/O error, dev sdb, sector 0
[10459.960278] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10459.960288] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10459.960296] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10459.960303] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 02 00 00 06 00
[10459.960321] end_request: I/O error, dev sdb, sector 2
[10460.101298] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10460.101308] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10460.101315] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10460.101321] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10460.101336] end_request: I/O error, dev sdb, sector 0
[10460.221405] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10460.221419] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10460.221434] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10460.221446] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[10460.221476] end_request: I/O error, dev sdb, sector 0
[10460.381284] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10460.381293] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10460.381300] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10460.381307] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 02 00 00 06 00
[10460.381321] end_request: I/O error, dev sdb, sector 2
[10460.501299] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10460.501308] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10460.501315] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10460.501322] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10460.501336] end_request: I/O error, dev sdb, sector 0
[10460.621287] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10460.621296] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10460.621303] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10460.621310] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[10460.621324] end_request: I/O error, dev sdb, sector 0
[10460.861286] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10460.861295] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10460.861302] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10460.861309] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 02 00 00 06 00
[10460.861323] end_request: I/O error, dev sdb, sector 2
[10461.061925] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10461.061940] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10461.061955] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10461.061972] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[10461.061996] end_request: I/O error, dev sdb, sector 8
[10461.062008] quiet_error: 158 callbacks suppressed
[10461.062014] Buffer I/O error on device sdb, logical block 8
[10461.062024] Buffer I/O error on device sdb, logical block 9
[10461.062029] Buffer I/O error on device sdb, logical block 10
[10461.062035] Buffer I/O error on device sdb, logical block 11
[10461.062040] Buffer I/O error on device sdb, logical block 12
[10461.062046] Buffer I/O error on device sdb, logical block 13
[10461.062051] Buffer I/O error on device sdb, logical block 14
[10461.062057] Buffer I/O error on device sdb, logical block 15
[10461.261280] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10461.261287] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10461.261292] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10461.261296] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 01 00
[10461.261305] end_request: I/O error, dev sdb, sector 8
[10461.261309] Buffer I/O error on device sdb, logical block 8
[10461.461288] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10461.461297] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10461.461304] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10461.461311] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 09 00 00 07 00
[10461.461325] end_request: I/O error, dev sdb, sector 9
[10461.461332] Buffer I/O error on device sdb, logical block 9
[10461.581289] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10461.581298] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10461.581305] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10461.581312] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[10461.581326] end_request: I/O error, dev sdb, sector 8
[10461.701290] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10461.701299] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10461.701306] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10461.701313] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[10461.701327] end_request: I/O error, dev sdb, sector 8
[10461.821286] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10461.821295] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10461.821302] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10461.821308] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[10461.821322] end_request: I/O error, dev sdb, sector 24
[10462.061290] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10462.061299] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10462.061306] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10462.061313] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[10462.061327] end_request: I/O error, dev sdb, sector 24
[10462.300678] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10462.300691] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10462.300697] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10462.300702] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[10462.300713] end_request: I/O error, dev sdb, sector 24
[10462.521305] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10462.521318] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10462.521330] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10462.521336] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[10462.521351] end_request: I/O error, dev sdb, sector 24
[10462.721288] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10462.721297] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10462.721305] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10462.721311] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[10462.721326] end_request: I/O error, dev sdb, sector 56
[10462.961292] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10462.961301] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10462.961309] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10462.961316] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[10462.961335] end_request: I/O error, dev sdb, sector 56
[10463.180056] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10463.180065] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10463.180072] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10463.180079] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[10463.180098] end_request: I/O error, dev sdb, sector 56
[10463.401297] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10463.401307] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10463.401314] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10463.401321] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[10463.401335] end_request: I/O error, dev sdb, sector 56
[10463.561293] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10463.561302] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10463.561309] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10463.561315] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[10463.561330] end_request: I/O error, dev sdb, sector 120
[10463.780116] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10463.780123] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10463.780129] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10463.780134] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[10463.780145] end_request: I/O error, dev sdb, sector 120
[10463.900747] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10463.900757] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10463.900764] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10463.900770] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[10463.900788] end_request: I/O error, dev sdb, sector 120
[10464.061302] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10464.061311] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10464.061318] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10464.061325] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[10464.061340] end_request: I/O error, dev sdb, sector 120
[10464.181441] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10464.181455] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10464.181470] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10464.181482] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10464.181512] end_request: I/O error, dev sdb, sector 0
[10464.321303] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10464.321317] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10464.321329] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10464.321341] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[10464.321371] end_request: I/O error, dev sdb, sector 0
[10464.481306] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10464.481321] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10464.481336] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10464.481354] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 01 00 00 07 00
[10464.481377] end_request: I/O error, dev sdb, sector 1
[10464.621451] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10464.621465] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10464.621480] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10464.621492] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[10464.621521] end_request: I/O error, dev sdb, sector 8
[10464.760541] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10464.760550] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10464.760557] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10464.760564] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 06 00
[10464.760578] end_request: I/O error, dev sdb, sector 8
[10464.881293] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10464.881308] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10464.881323] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10464.881334] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 0e 00 00 02 00
[10464.881364] end_request: I/O error, dev sdb, sector 14
[10465.041288] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10465.041306] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10465.041321] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10465.041332] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[10465.041362] end_request: I/O error, dev sdb, sector 24
[10465.201289] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10465.201307] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10465.201322] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10465.201333] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 01 00
[10465.201363] end_request: I/O error, dev sdb, sector 24
[10465.441319] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10465.441333] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10465.441348] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10465.441360] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 19 00 00 07 00
[10465.441387] end_request: I/O error, dev sdb, sector 25
[10465.660926] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10465.660935] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10465.660942] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10465.660952] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[10465.660960] end_request: I/O error, dev sdb, sector 56
[10465.881287] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10465.881301] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10465.881316] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10465.881328] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[10465.881358] end_request: I/O error, dev sdb, sector 56
[10466.081292] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10466.081309] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10466.081324] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10466.081336] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[10466.081365] end_request: I/O error, dev sdb, sector 120
[10466.081374] quiet_error: 182 callbacks suppressed
[10466.081381] Buffer I/O error on device sdb, logical block 120
[10466.081392] Buffer I/O error on device sdb, logical block 121
[10466.081400] Buffer I/O error on device sdb, logical block 122
[10466.081407] Buffer I/O error on device sdb, logical block 123
[10466.081414] Buffer I/O error on device sdb, logical block 124
[10466.081420] Buffer I/O error on device sdb, logical block 125
[10466.081427] Buffer I/O error on device sdb, logical block 126
[10466.081434] Buffer I/O error on device sdb, logical block 127
[10466.281284] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10466.281294] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10466.281309] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10466.281320] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 02 00
[10466.281354] end_request: I/O error, dev sdb, sector 120
[10466.281362] Buffer I/O error on device sdb, logical block 120
[10466.281371] Buffer I/O error on device sdb, logical block 121
[10466.481312] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10466.481327] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10466.481339] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10466.481351] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 7a 00 00 06 00
[10466.481380] end_request: I/O error, dev sdb, sector 122
[10466.701272] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10466.701281] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10466.701288] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10466.701294] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10466.701309] end_request: I/O error, dev sdb, sector 0
[10466.901289] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10466.901298] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10466.901311] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10466.901323] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10466.901354] end_request: I/O error, dev sdb, sector 0
[10467.101293] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10467.101302] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10467.101318] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10467.101330] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10467.101359] end_request: I/O error, dev sdb, sector 0
[10467.321287] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10467.321296] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10467.321303] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10467.321315] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[10467.321347] end_request: I/O error, dev sdb, sector 0
[10467.541289] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10467.541298] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10467.541305] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10467.541316] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 01 00 00 07 00
[10467.541346] end_request: I/O error, dev sdb, sector 1
[10467.761301] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10467.761310] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10467.761331] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10467.761342] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[10467.761372] end_request: I/O error, dev sdb, sector 0
[10467.921295] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10467.921304] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10467.921311] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10467.921328] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[10467.921355] end_request: I/O error, dev sdb, sector 0
[10468.141286] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10468.141294] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10468.141300] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10468.141305] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 02 00 00 06 00
[10468.141316] end_request: I/O error, dev sdb, sector 2
[10468.381289] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10468.381298] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[10468.381305] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[10468.381312] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[10468.381339] end_request: I/O error, dev sdb, sector 16[/B][/COLOR]


I am not sure that there is an issue with hardware compatibility as the Ext HD was working fine couple of weeks back..!

Cheers !!

---

### Post by piratebill on 2012-03-16
```
[10466.081381] Buffer I/O error on device sdb, logical block 120
```

Sounds like the drive died.  You said that this drive also fails on windows?  If it fails on another computer, it is for sure dead.  :(

Are comfortable removing the drive from the enclosure and hooking it into your computer?  If your lucky it might only be the enclosure thats wonky.

---

### Post by harivittal.hk on 2012-03-16
Hmmm unusual thing but never expected !! :(  So let me just plug into another system and check it out in that case..

btw could you kindly elaborate on the enclosure process mentioned..I didnt get that completely !!

Thanks !! Cheers !! :)

---

### Post by piratebill on 2012-03-16
> **harivittal.hk said:**
> Hmmm unusual thing but never expected !! :(  So let me just plug into another system and check it out in that case..

btw could you kindly elaborate on the enclosure process mentioned..I didnt get that completely !!

Thanks !! Cheers !! :)

I can try.  Inside the enclosure is a SATA (or if its really old an IDE) hard drive.  I'll assume your drive is SATA (SATA being the type of connection or plug that the drive has on it).  So if you take the drive out of the enclosure and open your computer (assuming its a desktop) you will find cables (hopefully) that can plug into your drive.  They look like this [http://www.sierra-cables.com/Cables/Images/SATA-Signal-Cable-1.jpg](http://www.sierra-cables.com/Cables/Images/SATA-Signal-Cable-1.jpg)

Basically we bypass the enclosure and directly plug the drive in.

---

### Post by harivittal.hk on 2012-03-16
> **piratebill said:**
> I can try.  Inside the enclosure is a SATA (or if its really old an IDE) hard drive.  I'll assume your drive is SATA (SATA being the type of connection or plug that the drive has on it).  So if you take the drive out of the enclosure and open your computer (assuming its a desktop) you will find cables (hopefully) that can plug into your drive.  They look like this [http://www.sierra-cables.com/Cables/Images/SATA-Signal-Cable-1.jpg](http://www.sierra-cables.com/Cables/Images/SATA-Signal-Cable-1.jpg)

Basically we bypass the enclosure and directly plug the drive in.

Thanks for this workaround !! I will have a go at it and we will see, where the fault lies, yes you are correct, am using a desktop at the moment.

I will come up with updates and keep this issue posted !!

Thanks for your valuable time again !!

Cheers !! Good Day !! :)

---

### Post by piratebill on 2012-03-16
I forgot to add, only plug the drive directly in when the computer is OFF!

---

