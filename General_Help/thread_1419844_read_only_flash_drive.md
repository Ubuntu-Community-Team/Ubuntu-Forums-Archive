---
title: "read only flash drive"
date: 2010-03-02
forum: General Help
---

### Post by mbjj11 on 2010-03-02
I bought a 16 gig flash drive straight from the manufacturer in China.  I am using Super OS 9.10.  I was using it previously without problems.  Then there was a mounting glitch when I put it in the other day and now the whole drive is read only.  It used to mount as a recognized 16 gig drive and it always removed safely when I took it out.  But this time all of that is gone.  It mounts now as "body></ht" [remove the quotes] and it will not unmount giving me an error message of "one or more volumes on the media are busy".  I tried going into windoze to uncheck the read only attribute but XP does not give me the security tab to access the attributes.  I've tried various tools and have read several threads here and elsewhere to try and fix this but nothing is working.  I keep getting messages telling me the drive is read only and I can't format it.  I've even tried changing the fstab entry to allow rw permissions all to no avail. Gparted won't allow me to do anything with it either.  Any ideas on how to get this drive off read only and back to normal would be appreciated. I don't care about losing the data as I already have it backed up.  I just want to use the drive again. There are no read/write switch tabs on the drive itself.  It all has to be done through programming.  thanks

---

### Post by RMZindorf on 2010-03-02
16 GB Flash Drive, rather large. But, also rather slow. What happens when you try and mount a 2, 4, or 8 GB Drive? What is the drive formated as?

---

### Post by mbjj11 on 2010-03-02
I don't have anything smaller than 16 gigs.  I have a kingston but it's even bigger @64.  When I used it, it mounted without problems.  But now I don't want to try and mount it as I think 9.10 may be the issue.  I use the 64 gig on a machine with 8.10 installed and have no problems at all.  The 16 gig is a fat32 file system.  I'd really like to format it in ext3 if I can ever get the write protect turned off.

---

### Post by scouser73 on 2010-03-02
> **mbjj11 said:**
> I bought a 16 gig flash drive straight from the manufacturer in China.  I am using Super OS 9.10.  I was using it previously without problems.  Then there was a mounting glitch when I put it in the other day and now the whole drive is read only.  It used to mount as a recognized 16 gig drive and it always removed safely when I took it out.  But this time all of that is gone.  It mounts now as "body></ht" [remove the quotes] and it will not unmount giving me an error message of "one or more volumes on the media are busy".  I tried going into windoze to uncheck the read only attribute but XP does not give me the security tab to access the attributes.  I've tried various tools and have read several threads here and elsewhere to try and fix this but nothing is working.  I keep getting messages telling me the drive is read only and I can't format it.  I've even tried changing the fstab entry to allow rw permissions all to no avail. Gparted won't allow me to do anything with it either.  Any ideas on how to get this drive off read only and back to normal would be appreciated. I don't care about losing the data as I already have it backed up.  I just want to use the drive again. There are no read/write switch tabs on the drive itself.  It all has to be done through programming.  thanks

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by mbjj11 on 2010-03-02
Well ... that didn't work either.  I was able to change ownership to me and change to read and write on the files.  Then when I tried to change the group settings I was still locked out and was told the settings couldn't be changed because it's a read only device.  This is frustrating.

---

### Post by dcstar on 2010-03-02
> **mbjj11 said:**
> Well ... that didn't work either.  I was able to change ownership to me and change to read and write on the files.  Then when I tried to change the group settings I was still locked out and was told the settings couldn't be changed because it's a read only device.  This is frustrating.

USB sticks sold with crap Windows ISO images on them are detected as CD-ROMS - which are Read Only devices.

You have to rewrite the partition table (which will totally wipe the device) using the Partition Manager after you unmount the device.

---

### Post by mbjj11 on 2010-03-02
Once I mount this thing, it won't unmount.  I get a message saying the device is busy preventing it from unmounting.  Every partition program I've used won't access the drive.  I've used gparted here and partition magic on the XP side and I still can't change anything.
I'm beginning to think the drive can't be changed and I am hesitant to use any flash drive in this box fearing the same thing will happen again.  8.10 has no problems mounting and unmounting the drives even though this one is useless on that box too.

---

