---
title: "Unable to create RAID 0 with mdadm"
date: 2010-01-18
forum: General Help
---

### Post by rswing on 2010-01-18
So I have searched the forums for weeks now, and I cannot seem to figure out my issue.

I am running Mythbuntu 9.10 64 bit.

I have a small HD that runs the OS, and I want to create a large RAID array for my video storage. I have 4x1TB drives that I would like to put into a software RAID, however no matter what I do, 2 of the drives are always busy and I cannot seem to kill whatever process has them "busy"

I used to have 2 of the drives in a dmraid array, however I have removed them from the array, and uninstalled dmraid. I have reinstalled the OS multiple times with many different attempts to get the drives working again.

Even gparted is unable to format the drives because they are in use. I am able to "create new partition table" but I can only format the first of the 4 large drives (sdb, sdc, sdd, sde) the other 3 fail to format.

When I try to create a new mdadm array, I get the folowwinf error...

# mdadm --create /dev/md/md0 --chunk=4 --level=0 --raid-devices=4 /dev/sdb /dev/sdc /dev/sdd /dev/sde

mdadm: Cannot open /dev/sdc: Device or resource busy
mdadm: create aborted


Does anyone have any advice for me? I feel like Ubuntu still thinks that there is some type of RAID that is using the disks, but I cannot figure out what...the fact that the drives are unmounted and still will not format worries me :-(

Thanks in advance!

---

### Post by pirateghost on 2010-01-18
how are you formatting them?

maybe your machine still has them mounted?  have you rebooted since you got rid of dmraid?

i would, however recommend HIGHLY AGAINST, using 4x1tb in a RAID0.  if one drive fails, you lose all your data.  consider a RAID5 setup instead

---

### Post by rswing on 2010-01-18
Thanks for the reply, I understand and agree that a RAID0 is not ideal.

However I am unable to create any type of RAID array using mdadm.

I have restarted since removing dmraid...and then I run "mount" it does not show the devices mounted. Also in gparted, the devices do not show as mounted.

I removed dmraid using "apt-get remove dmraid" is this the proper and complete way to do this, or is there a better way to remove it?

Thanks again!

---

### Post by Fire_Chief on 2010-01-18
You may want to double check the Motherboard BIOS and verify that there is no onboard "RAID" controller which may be enabled and trying to use two of the disks.
Found another user who mentioned the same problem and noted that the onboard Nvidia RAID controller was enabled. Linux detected it upon install and automatically added dmraid to manage it. Details found [here]("http://www.righteoushack.net/?p=197")

Cheers!

---

### Post by rswing on 2010-01-18
Ok, thank you all for your help! I have finally figured it out!

There was something in the boot sector that dmraid must have used and even with dmraid uninstalled the OS viewed the disk as in use.

By clearing the boot sector on all 4 drives...

dd if=/dev/zero of=/dev/sdb bs=512 count=1

I was able to then restart the computer and then assemble a raid using all 4 drives! 

Thank you all for your help!!!

---

