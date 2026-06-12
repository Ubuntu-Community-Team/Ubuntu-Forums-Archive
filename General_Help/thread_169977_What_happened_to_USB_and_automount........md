---
title: "What happened to USB and automount......."
date: 2006-05-03
forum: General Help
---

### Post by strfmstr on 2006-05-03
Until recently, automount has worked flawlessly for all my usb sticks (Lexar and Kingston). Now, whenever I plug them in, I have to mount them manually (as root of course).

Here is the output for the Kingston:

[  904.799734] usb 3-1: new high speed USB device using ehci_hcd and address 20
[  904.839424] scsi18 : SCSI emulation for USB Mass Storage devices
[  904.840097] usb-storage: device found at 20
[  904.840100] usb-storage: waiting for device to settle before scanning
[  906.503216]   Vendor: Kingston  Model: DataTraveler 2.0  Rev: 1.04
[  906.503222]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  906.598197] SCSI device sda: 1003520 512-byte hdwr sectors (514 MB)
[  906.598361] sda: Write Protect is off
[  906.598363] sda: Mode Sense: 23 00 00 00
[  906.598365] sda: assuming drive cache: write through
[  906.599694] SCSI device sda: 1003520 512-byte hdwr sectors (514 MB)
[  906.599863] sda: Write Protect is off
[  906.599866] sda: Mode Sense: 23 00 00 00
[  906.599867] sda: assuming drive cache: write through
[  906.599869]  /dev/scsi/host18/bus0/target0/lun0: p1
[  906.600664] Attached scsi removable disk sda at scsi18, channel 0, id 0, lun 0
[  906.601328] usb-storage: device scan complete

and for the Lexar Trio:

[  929.247379] usb 3-1: new high speed USB device using ehci_hcd and address 21
[  929.279199] scsi19 : SCSI emulation for USB Mass Storage devices
[  929.279710] usb-storage: device found at 21
[  929.279713] usb-storage: waiting for device to settle before scanning
[  930.943209]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9144
[  930.943216]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  931.014394] SCSI device sda: 245504 512-byte hdwr sectors (126 MB)
[  931.014850] sda: Write Protect is off
[  931.014853] sda: Mode Sense: 02 00 00 00
[  931.014854] sda: assuming drive cache: write through
[  931.016387] SCSI device sda: 245504 512-byte hdwr sectors (126 MB)
[  931.016847] sda: Write Protect is off
[  931.016849] sda: Mode Sense: 02 00 00 00
[  931.016851] sda: assuming drive cache: write through
[  931.016853]  /dev/scsi/host19/bus0/target0/lun0: p1
[  931.017866] Attached scsi removable disk sda at scsi19, channel 0, id 0, lun 0
[  931.018588] usb-storage: device scan complete

I have gone back and verified I have not changed anything that would present this type of behaviour.

I am wondering if there is an update that may have caused this. Is there a way for synaptic to provide an update history?

Any insight anyone could provide would be great.

TIA.

---

### Post by viroos on 2006-05-03
first of all: this is my first post on this forum so Hi all :-)
secend: I have thesame problem

I'm using xubuntu 6.06 beta 2
my dmesg outpu:
```
[  616.312926] usb 3-1: new high speed USB device using ehci_hcd and address 3
[  616.372777] scsi1 : SCSI emulation for USB Mass Storage devices
[  616.372856] usb-storage: device found at 3
[  616.372858] usb-storage: waiting for device to settle before scanning
[  618.871656]   Vendor: USB       Model: BAR               Rev: 2.00
[  618.871667]   Type:   Direct-Access                      ANSI SCSI revision: 02
[  619.946472] ready
[  619.946972] SCSI device sda: 1024000 512-byte hdwr sectors (524 MB)
[  619.947490] sda: Write Protect is off
[  619.947494] sda: Mode Sense: 03 00 00 00
[  619.947496] sda: assuming drive cache: write through
[  619.949218] SCSI device sda: 1024000 512-byte hdwr sectors (524 MB)
[  619.949738] sda: Write Protect is off
[  619.949742] sda: Mode Sense: 03 00 00 00
[  619.949744] sda: assuming drive cache: write through
[  619.949747]  sda: sda1
[  619.950398] sd 1:0:0:0: Attached scsi removable disk sda
[  619.950438] sd 1:0:0:0: Attached scsi generic sg0 type 0
[  619.951334] usb-storage: device scan complete
```

I'm using Actina 512 MB pen drive.

I hope some one will help fix it soon.

best regards viroos

---

### Post by strfmstr on 2006-05-04
bump

---

### Post by wylfing on 2006-05-11
Read here:

[http://www.ubuntuforums.org/showthread.php?t=173300](http://www.ubuntuforums.org/showthread.php?t=173300)

---

### Post by Harrkev on 2006-05-12
I am having the same problem.  USB devices are gived SDx1 designaltions, but they do not mount.](*,) 

Wylfing...

Thank you for that link that you provided.  To a person with more experience, that might be helpful.  By reading that, I understand that I need to do something to dbus, hal and pmount.  He said "re-install."  To me, that means:

1) Go to Synaptic, and remove all of these items.
2) Then, go back into Synaptic and re-add all of them.

That sounds dangerous to me.  Unless I am mistaken, somewhere between step 1 and step 2 my system should crash rather spectacularly...

Can you break it down for dummies?

---

### Post by almostlinux on 2006-05-13
Harrkey,

once in synaptic, you can just 'right click' -> 'Reinstall'

---

### Post by Harrkev on 2006-05-13
Wow.  You rock.  Worked like a charm.  Thanks a lot.

But that brings me to another question...

How do I turn off caching???  I just tried it out, and found out that if I deleted a file and yanked the drive out, the file shows back up when inserted.  I have to manually unmount the drive to commit the changes.  Is there a way to have all changes happen instantly?

Yeah, I know that this will cause a performance hit, and also that you are SUPPOSED to unmount them first.  But who actually has the dicipline to do this with a USB flash drive? :-D 

Thanks.

---

### Post by TheReaperD on 2007-07-10
> **Harrkev said:**
> 

How do I turn off caching???  I just tried it out, and found out that if I deleted a file and yanked the drive out, the file shows back up when inserted.  I have to manually unmount the drive to commit the changes.  Is there a way to have all changes happen instantly?

Yeah, I know that this will cause a performance hit, and also that you are SUPPOSED to unmount them first.  But who actually has the dicipline to do this with a USB flash drive? :-D 



Amen.  Anyone have any suggestions for turning off write caching on an automounting removable drive (such as a USB flash drive)?  I'd rather know exactly when files are done copying to it instead of it telling me that it's done when it is not.

Thank you in advance.

---

### Post by dabl on 2007-07-10
> **TheReaperD said:**
> Amen.  Anyone have any suggestions for turning off write caching on an automounting removable drive (such as a USB flash drive)? 

I don't know about turning off caching, but you can get the same result by simply right-clicking the device and choosing "Safely Remove" or "Eject" or whatever it gives you regarding "planned removal" (as opposed to "yanking").

---

### Post by TheReaperD on 2007-07-10
> **dabl said:**
> I don't know about turning off caching, but you can get the same result by simply right-clicking the device and choosing "Safely Remove" or "Eject" or whatever it gives you regarding "planned removal" (as opposed to "yanking").

The problem I'm running into, a lot, right now is that I am copying multiple hundred megabytes of data and the only way I can tell it's done is by looking at the little light on my flash drive.  The actual copy dialog finishes up to 5 to 10 minutes earlier.

And, I can't select to umount the disk until after the copy is complete.  So, I have to keep coming back to this computer so I can look at the light on my USB drive because I can't see it from other computers I am working on.  (But I can see the copy dialog box when it is up.)

I know it's a minor thing but, with the project I am currently doing, it's really annoying.

---

### Post by dabl on 2007-07-10
NTFS, ext3, reiserfs, and other high-performance filesystems are "journalling" filesystems.  They run a quasi-realtime transaction log, in order to be able to repair themselves in the event of a power outage or crash.  But the transactions themselves (reads and writes) don't happen in realtime, unless forced by the "Safely Remove", "Eject", or "Unmount" commands.  I'm not sure you can rely on the blinky light to know whether all pending transactions have been completed or not .... :confused:

---

