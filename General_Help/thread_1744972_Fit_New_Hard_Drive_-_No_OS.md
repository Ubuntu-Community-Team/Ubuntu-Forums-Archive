---
title: "Fit New Hard Drive - No O/S"
date: 2011-04-30
forum: General Help
---

### Post by HostPost on 2011-04-30
Hi,
I have a new clean unused hard drive I need to fit to a Dell Inspiron desktop PC and set up Ubuntu on (I have a flash drive with 101.10 on it).

I have never fitted a fresh new H/D before with no O/S running on it. But i guess there is a set up I am missing somewhere.

I have the drive in and connected but on start up it loads the front dell screen but proceeds no further. I can not get to the start menu or boot record.

What am I missing there please?

regards

---

### Post by mike555 on 2011-04-30
"clean ,unused hard drive" ...... what do you expect to boot into?

---

### Post by 3Miro on 2011-04-30
Plug the flash drive in and tell the BIOS to boot from the flash drive. You obviously cannot boot from an empty hard-drive.

---

### Post by HostPost on 2011-04-30
Thanks for the replies. Yes I know that the drive won't boot as there is nothing on it. I had the Unbuntu USB stick drive plugged in at the time. I thought it would boot direct from that. But it don't and I can not get to the bios to tell it to do anything.

Not sure how else to get it going.

---

### Post by oldfred on 2011-04-30
How old is system? About 4 or 5 years ago they stopped including floppy drives and everyone wondered how to boot an external, so they modified BIOS to boot USB devices.

Do you have working CD?

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

But do not create /boot unless real old system with 137GB BIOS boot limit.
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by 3Miro on 2011-04-30
> **HostPost said:**
> Thanks for the replies. Yes I know that the drive won't boot as there is nothing on it. I had the Unbuntu USB stick drive plugged in at the time. I thought it would boot direct from that. But it don't and I can not get to the bios to tell it to do anything.

Not sure how else to get it going.

Check your BIOS settings. On some computers you can hit F12 during boot and that will let you chose where do you want to boot from. Usually if you hit "del" you can enter the BIOS settings and set the boot order from there. Something along those lines:

[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

---

### Post by HostPost on 2011-04-30
Thanks. It is newer than 4-5 years for sure. It don't have a floppy but does have a CD. I don't have a Ubuntu CD though - only the USB.

Not sure what the bios spec is.

---

### Post by Rich_B_uk on 2011-04-30
So mate, easy fix this...

When you turn on your PC it'll run through a series of POST checks in the BIOS and then onto the system booting. Part of the BIOS' job is to store the choice for what drive/source media you want to boot from!

By default it tends to prioritise hard drives, so all you need to do is to enter the BIOS and change the boot order (make sure you have your flash drive plugged in at this point as it will often refer to the drive by it's volume label)

To enter the BIOS either read your manual, look it up, or guess. Hammer the following popular keys repeatedly at startup:

Delete, F2, F4, F8, F10, F12

---

### Post by oldfred on 2011-04-30
On my computer I had all the USB boot options under f12 or BIOS settings, USB floppy, USB CD even USB hard drive. 
But my flash drive was seen as a hard drive and it only sees the flash drive under the list of hard drives not USB devices.

---

### Post by HostPost on 2011-04-30
Cheers,
I'll give it another go. It did not accept F2 or F12 as said on the start screen. I did not try the others or esc though.

Failing this I guess I could put my knack'd old win H/D back in and use that to boot it and write the USB to the new drive fitted as a slave.

---

### Post by 3Miro on 2011-04-30
Del should work.

---

