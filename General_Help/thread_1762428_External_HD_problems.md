---
title: "External HD problems"
date: 2011-05-19
forum: General Help
---

### Post by RogerD on 2011-05-19
Help

Having problems with external hard drives. I may be wrong, but I suspect they originated with an upgrade to 10.04 last Christmas. Around that time I also started using Amazon's S3 storage system, and, as a consequence, I stopped using my WD 80G external drive, previously used to backup my important files. 

A week or so ago I decided to start using the WD drive again. I can't remember exactly what I did, but it wasn't happy - never caused any problems before. When I plug it in, the on-off light as the front keeps flashing on and off, and when I try to remove the drive I get the message:

Error unmounting volumne
An error occured while performing an operation on "My Book" (Partition 1 of WD 800BB External): The device is busy

Details: Cannot unmount because file system on device is busy

Assuming the device had died - it's about 5 years old - I bought a 160G Samsung S-Series drive - my but they do look neat! Unfortunately, this doesn't seem to have solved my problem.

I plugged the new  drive in, and it happily appeared on my desktop. It seemed a good idea at the time, but I then started to format the drive - using the default option of FAT. All went well at first, but then the format process stopped.

My new Samsung drive now seems to be operating pretty much as the WD device, I  can't copy to the drive, and attempts to unmount it generate a response similar to what's happening with the WD drive. Currently, although plugged in, I can't see the  drive on my desktop, although it appears under Places. However, when I try to mount the drive, I get the message:

Unable to mount SAMSUNG
A job is pending on /dev/sdb1

Any ideas, anybody?

Roger D

---

### Post by jerrrys on 2011-05-19
im thinking you should try NTFS.  i assume your using FAT to maintain compatibility with windows.

myself, i have a similar setup using ext4 on a non-boot hdd

also there are a couple of NTFS compatibility packages in synaptic

---

