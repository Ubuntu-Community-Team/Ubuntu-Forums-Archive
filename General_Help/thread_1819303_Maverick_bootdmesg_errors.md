---
title: "Maverick boot/dmesg errors"
date: 2011-08-05
forum: General Help
---

### Post by ninhalo5 on 2011-08-05
Hi all, I'm having a problem; a little while ago I was working in Gimp and my computer decided to freeze up. The only way I could reboot it was to hold the power button in and do a hard shutdown.
after I rebooted it went to a black screen with a rapid flashing cursor thing and would just stay there; after several reboots Grub loaded (only have Ubuntu installed usually I never see Grub) from there I could only launch from the recovery option during the launch a slew of errors would kick out
```
[   13.876271] sd 10:0:0:3: [sde] Attached SCSI removable disk
[   13.877529] sd 10:0:0:2: [sdd] 3862528 512-byte logical blocks: (1.97 GB/1.84
 GiB)
[   13.878284] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[   13.879958] sd 10:0:0:1: [sdc] Attached SCSI removable disk
[   13.880644] sd 10:0:0:2: [sdd] Write Protect is off
[   13.880648] sd 10:0:0:2: [sdd] Mode Sense: 03 00 00 00
[   13.880651] sd 10:0:0:2: [sdd] Assuming drive cache: write through
[   13.884298] sd 10:0:0:2: [sdd] Assuming drive cache: write through
[   13.884303]  sdd:
[   14.195511] sd 10:0:0:2: [sdd] Unhandled sense code
[   14.195515] sd 10:0:0:2: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   14.195520] sd 10:0:0:2: [sdd] Sense Key : Hardware Error [current] 
[   14.195524] sd 10:0:0:2: [sdd] Add. Sense: No additional sense information
[   14.195529] sd 10:0:0:2: [sdd] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.195538] end_request: I/O error, dev sdd, sector 0
[   14.195542] Buffer I/O error on device sdd, logical block 0
[   14.504726] sd 10:0:0:2: [sdd] Unhandled sense code
[   14.504730] sd 10:0:0:2: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   13.877529] sd 10:0:0:2: [sdd] 3862528 512-byte logical blocks: (1.97 GB/1.84
 GiB)
[   13.878284] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[   13.879958] sd 10:0:0:1: [sdc] Attached SCSI removable disk
[   13.880644] sd 10:0:0:2: [sdd] Write Protect is off
[   13.880648] sd 10:0:0:2: [sdd] Mode Sense: 03 00 00 00
[   13.880651] sd 10:0:0:2: [sdd] Assuming drive cache: write through
[   13.884298] sd 10:0:0:2: [sdd] Assuming drive cache: write through
[   13.884303]  sdd:
[   14.195511] sd 10:0:0:2: [sdd] Unhandled sense code
[   14.195515] sd 10:0:0:2: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   14.195520] sd 10:0:0:2: [sdd] Sense Key : Hardware Error [current] 
[   14.195524] sd 10:0:0:2: [sdd] Add. Sense: No additional sense information
[   14.195529] sd 10:0:0:2: [sdd] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   14.195538] end_request: I/O error, dev sdd, sector 0
[   14.195542] Buffer I/O error on device sdd, logical block 0
[   14.504726] sd 10:0:0:2: [sdd] Unhandled sense code
[   14.504730] sd 10:0:0:2: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   14.504734] sd 10:0:0:2: [sdd] Sense Key : Hardware Error [current] 
[   14.504738] sd 10:0:0:2: [sdd] Add. Sense: No additional sense information
[   14.504742] sd 10:0:0:2: [sdd] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
```These errors go on for about 1000 more lines repeating the same thing except the number in the brackets changes. This is the same readout I'm getting with dmesg.
Once I'm able to log in through recovery mode I put in gdm start and get to  X. When I sign in there I get a pop-up warning me about xfce power manager is either running or locked up then it closes and I'm in.
Now that I've actually logged in I went ahead and shut down the proper way. once I reboot the computer will load but that black screen with the flashing cursor will stay for about 5 minutes then I'll get the ugly blue kubuntu screen then all of that code will start processing over top of the splash.

any one have an idea of what is going on here? I've tried to google the error but it never comes back sdd  it's always sda or sdb. I'm imagining maybe my HDD is dying now :(  though I haven't got a error for it on the desktop as I have before.

Thanks guys

---

### Post by wildmanne39 on 2011-08-05
Hi, a hard reset is a bad idea, I think you caused by sectors on your hard drive. Open disk utility and run a smart test and see if you have bad sectors.

Here is a way to safely shutdown a frozen system.

That is - hold down Alt+PrintScreen, and then press R-E-I-S-U-B slowly, one after the other. On some keyboards/systems, you need to use the AltGr key. 

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by ninhalo5 on 2011-08-06
Hi thanks for the reply. Yes I know a hard shutdown is bad but I really didn't have a choice everything was locked up including the keyboard and mouse. Guess whatever happened really did a number. The disk scan utility came back inclusive well rather it wouldn't run. I did however unplug the built in sd card reader and the sdd error went away. Now when I try logging in I need to put my info on a command line then it will log me in. Guess a setting got changed, time to figure that one out :)

---

