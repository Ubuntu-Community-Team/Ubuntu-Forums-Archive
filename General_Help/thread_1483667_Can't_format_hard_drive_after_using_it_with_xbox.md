---
title: "Can't format hard drive after using it with xbox"
date: 2010-05-14
forum: General Help
---

### Post by Infamshxr on 2010-05-14
Hello, I have an 80gb hard drive that I used in an xbox for xbmc and it was formatted to whatever it needed to be formatted to for it. Now that I want to use it in my computer, I can't format it back to ext4 or NTFS. It's somewhat recognized, but the partition shows up as unknown. Is there a program that I can get to reformat it? idk if gparted will work cuz it won't startup on the live CD. I will give it a shot once I install ubuntu onto the computer. Thanks in advance.

---

### Post by srs5694 on 2010-05-14
Please post the results of typing "sudo fdisk -l" at a command prompt on your computer. Please post these results between the strings "[noparse]```
[/noparse]" and "[noparse]
```[/noparse]" to improve legibility.

---

### Post by Infamshxr on 2010-05-17
ell after installing 9.10 the computer wouldn't boot til I took out the hard drive, so I took it out then put it in my external enclosure. After doing that, it doesn't show up anywhere. Not in the fdisk nor in the disk utility... Any ideas? :confused:

---

### Post by srs5694 on 2010-05-17
Unplug the disk, then type "dmesg" at a shell prompt. Plug the disk in, wait a few seconds, and type "dmesg" again. Any new lines relate to the detection of the drive. If nothing appears, then the drive isn't being detected -- it's a hardware fault. If so, try swapping cables, re-attaching the drive inside its case, etc. Even if messages appear in dmesg, it could be a hardware fault, but posting the new messages might provide some clue about what the problem is. Also, try "ls /dev/[sh]d?" both before and a few seconds after plugging the device in. If no new entries appear, then the disk isn't being detected (again, a likely hardware fault, although there could be software issues like an inadequate driver).

---

### Post by Infamshxr on 2010-05-17
Ok, well I know its not a hardware failure cuz the hard drive worked fine until I formatted it for the xbox. But, here's what dmesg did.

Before I plugged in the hard drive:
```

[ 2628.076018] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 3 (-16).
[ 2752.608026] wlan0: no probe response from AP 00:18:39:85:f2:18 - disassociating
[ 2877.992248] wlan0: authenticate with AP 00:18:39:85:f2:18
[ 2877.993632] wlan0: authenticated
[ 2877.993635] wlan0: associate with AP 00:18:39:85:f2:18
[ 2877.996276] wlan0: RX ReassocResp from 00:18:39:85:f2:18 (capab=0x411 status=0 aid=3)
[ 2877.996281] wlan0: associated

```
(the first 2 lines of code was repeated like a million times.)

And then after:
```

[ 4356.693491] sd 5:0:0:0: [sdf] Add. Sense: No additional sense information
[ 4387.112022] usb 1-3: reset high speed USB device using ehci_hcd and address 4
[ 4387.253079] sd 5:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 4387.253087] sd 5:0:0:0: [sdf] Add. Sense: No additional sense information

```
(the first 2 lines and last 3 lines of code was repeated like a million times)

---

### Post by srs5694 on 2010-05-17
I think that you've got a hardware failure with either your external enclosure or possibly with your hard disk. As a comparison, here's what I get when I plug in a hard disk connected via a functioning external USB interface:

```

[154051.823045] usb 2-4: new high speed USB device using ehci_hcd and address 2
[154051.940163] usb 2-4: configuration #1 chosen from 1 choice
[154051.940571] scsi5 : SCSI emulation for USB Mass Storage devices
[154051.940808] usb-storage: device found at 2
[154051.940811] usb-storage: waiting for device to settle before scanning
[154056.940827] scsi 5:0:0:0: Direct-Access     WDC WD60 0AB-32BVA0       21.0 PQ: 0 ANSI: 0
[154056.940997] sd 5:0:0:0: Attached scsi generic sg2 type 0
[154056.941337] usb-storage: device scan complete
[154056.943310] sd 5:0:0:0: [sdb] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[154056.944056] sd 5:0:0:0: [sdb] Write Protect is off
[154056.944058] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[154056.944060] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[154056.945554] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[154056.945557]  sdb: sdb1 sdb2
[154057.012052] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[154057.012056] sd 5:0:0:0: [sdb] Attached SCSI disk

```

Your output, of course, wouldn't be identical to this, but there should be more similarities. The fact that you got a "Sense Key : No Sense" message is suspicious. I'm not intimately familiar with all the error messages, but that one sounds like it could be trouble.

---

### Post by Infamshxr on 2010-05-17
It's not the enclosure, I was just using it with another hard drive before I put in the problem drive. As far as the hard drive, like I said it worked fine before I reformatted it and used it in the xbox. Is there any disk utility that knows the same file system as the xbox file system?

---

### Post by ubername on 2010-05-17
Sod's law works such that hardware fails just after you have done something else unusual, making you sure it is not a HW problem (or that's what happens to me!)

Have you checked that the drive still works in the xbox?

---

### Post by Fenris_rising on 2010-05-17
The drive has been formatted to xfat. This is the xbox format. Your biggest problem however is that the hard drive is locked by the xbox. When the xbox is booted up it unlocks the HDD when it is shutdown it locks the HDD again.

I can't remember what the software was but under xbox in the afterdawn forums there is info on the apps needed to unlock the drive to make it usable again.

This involved making a live cd. Plug the HDD into the pc (make it the only one plugged in) boot via the live disk and a linux based system runs. You can then unlock the drive.

Other than that you could hook the drive back to the xbox turn it on and remove the drive whilst it is 'hot'.

I am assuming your using an xbox 1
regards

Fenris

---

### Post by Infamshxr on 2010-05-17
Yes! That's what the problem is. Totaly forgot about the locking thing. The software that I used was ndure 3.0. It was lost in the move but I'm sure I could find it. I wonder if that software could run under ubuntu, since it is linux based. I could always burn another copy when I have more time and give it a shot. You think that the ndure cd will be able to format the partition back to something readable or should I just delete the partition and leave it like that?

---

### Post by Fenris_rising on 2010-05-17
i think once you unlock it u should be able to format it as you wish

regards

Fenris

---

