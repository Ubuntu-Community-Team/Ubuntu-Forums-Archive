---
title: "Moving to larger hard drive, incorrect MBR"
date: 2009-10-08
forum: General Help
---

### Post by mobrien118 on 2009-10-08
Hi,

I used 'dd' on my Ubuntu box to migrate one (laptop) SATA Hard drive (60GB) to a new one (320GB).

After the procedure, the new drive boots in the laptop the original one came from, but EVERYTHING (Gparted, Windows disk manager, fdisk) thinks it is now a 60GB drive, so I can't enlarge the partitions.

Any ideas on how to update the MBR/Partition Table to reflect the true size of the disk?

Thanks!

--mobrien118

---

### Post by mechro on 2009-10-08
Hmm... it looks like you need the original MBR from the 320GB drive which you obviously now haven't got.

The only suggestion I have is to back up your installation and reformat the drive and if you reinstall using "dd" make sure to avoid writing over the MBR.

---

### Post by rbc on 2009-10-08
What’s the full dd command you used? And you’re not trying to enlarge the partition while running Ubuntu (not the LiveCD, but the Ubuntu installed to the hard drive), are you? If so, you cannot enlarge the partition while it’s mounted. Get a GParted Live CD, boot up and resize away

---

### Post by mobrien118 on 2009-10-09
> **rbc said:**
> What’s the full dd command you used? And you’re not trying to enlarge the partition while running Ubuntu (not the LiveCD, but the Ubuntu installed to the hard drive), are you? If so, you cannot enlarge the partition while it’s mounted. Get a GParted Live CD, boot up and resize away

sudo dd if=/dev/sdc of=/dev/sdd

damn. I guess I should have used the "bs=512" option. Is that right?

Surely, I can recover from this...right?

---

### Post by mobrien118 on 2009-10-09
> **mobrien118 said:**
> sudo dd if=/dev/sdc of=/dev/sdd

damn. I guess I should have used the "bs=512" option. Is that right?

Surely, I can recover from this...right?

Hmmmm... I guess not. As I ORIGINALLY thought, bs is the block size for copying. That should have no effect.

Looking back, I have done this before and always got an error that the MBR was  broken and the computer BIOS offered to fix it. In this case, no offer to fix it. Doesn't even know that it's broke'.

---

### Post by drs305 on 2009-10-09
I previously used Partimage. I if I cloned an image to a larger partition than the original there were times the system would think it was the smaller size.

I had to run "resize2fs" to allow the system to recognize the actual size of the partition. It's listed in the man pages, so read up and then do a search of the forums. I'd try to offer more assistance but I no longer use Partimage and it's been a long time since I used the resize2fs command.

---

### Post by mobrien118 on 2009-10-09
> **drs305 said:**
> I previously used Partimage. I if I cloned an image to a larger partition than the original there were times the system would think it was the smaller size.

I had to run "resize2fs" to allow the system to recognize the actual size of the partition. It's listed in the man pages, so read up and then do a search of the forums. I'd try to offer more assistance but I no longer use Partimage and it's been a long time since I used the resize2fs command.

Thanks for the suggestion, but the partition isn't the issue. it looks like the MBR thinks there is an incorrect number of cylinders. I tried to change it using fdisk, but I'm not sure of the correct number of cylinders. I used the formula 320GB/60GB *times* the currently specified number of cylinders (the other geometry is the same) but fdisk, although it said it was writing the MBR, didn't make the change.

Any suggestions on how I can get this hard drive back to the correct size again? Next time, I'll copy each partition separately and just use "fixmbr" on the XP boot disk to get it booting again.

Thanks!

---

### Post by fragos on 2009-10-09
I had problems using dd as well and managed to get things straitened out using the package testdisk -- run it in a terminal. Perhaps there's an answer for you with that.

---

### Post by mobrien118 on 2009-10-10
> **fragos said:**
> I had problems using dd as well and managed to get things straitened out using the package testdisk -- run it in a terminal. Perhaps there's an answer for you with that.

I think I've tried every possible option there and nothing will take. I've tried overwriting the cylinder spec, etc.

This is very rough. I want to use the whole 320GB! Is that too much to ask?!? :-)

Thanks for that, though. I'll probably use that tool in the future now that I know about it.

In the meantime, anyone else think of anything? This is a real stumper...

--mobrien118

---

### Post by dcstar on 2009-10-10
> **mobrien118 said:**
> Hi,

I used 'dd' on my Ubuntu box to migrate one (laptop) SATA Hard drive (60GB) to a new one (320GB).

After the procedure, the new drive boots in the laptop the original one came from, but EVERYTHING (Gparted, Windows disk manager, fdisk) thinks it is now a 60GB drive, so I can't enlarge the partitions.

Any ideas on how to update the MBR/Partition Table to reflect the true size of the disk?

Thanks!

--mobrien118

[http://www.faqs.org/docs/Linux-HOWTO/LILO-crash-rescue-HOWTO.html#partition_repair](http://www.faqs.org/docs/Linux-HOWTO/LILO-crash-rescue-HOWTO.html#partition_repair)

---

### Post by mechro on 2009-10-10
> **mobrien118 said:**
> I think I've tried every possible option there and nothing will take. I've tried overwriting the cylinder spec, etc.

This is very rough. I want to use the whole 320GB! Is that too much to ask?!? :-)

Thanks for that, though. I'll probably use that tool in the future now that I know about it.

In the meantime, anyone else think of anything? This is a real stumper...

--mobrien118

One possibility is to decrease the partition size as it is and when the MBR is rewritten by Gparted or whatever method you use the correct disk parameters might be scanned and entered.

---

### Post by mobrien118 on 2009-10-12
I figured this out.

I tried, seriously, every possible Linux tool to change the number of cylinders on the disk and had no success (I wonder why this didn't work, maybe Hitachi prevents changing drive parameters, but then why was I able to overwrite it in the first place?)

Anyway, what finally worked was using a Hitachi tool called "Feature Tool" (found at [http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)). This very easily allowed me to restore the drive back to its original size description, which it was incorrectly reporting to the BIOS.

@mercho: FYI: the problem wasn't with any partition, there were no partitions on the disk after I zeroed it out. It was with the drive describing itself as a different size.

I actually got a lot of help from LinuxForums, which if anyone is interrested in how I solved the problem, is loacted here: [http://www.linuxquestions.org/questions/linux-hardware-18/dd-copied-entire-disk-now-incorrect-size-reported-cant-fix-760852/](http://www.linuxquestions.org/questions/linux-hardware-18/dd-copied-entire-disk-now-incorrect-size-reported-cant-fix-760852/)

Thanks for any and all who tried to help!

---

### Post by mechro on 2009-10-13
> **mobrien118 said:**
> I figured this out.

Anyway, what finally worked was using a Hitachi tool called "Feature Tool" (found at [http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)). This very easily allowed me to restore the drive back to its original size description, which it was incorrectly reporting to the BIOS.


Thanks for any and all who tried to help!

Bugger! I've got that on my Ultimate Boot CD #-o ... never used it of course because I don't have Hitachi.

Glad you got it sorted.

---

