---
title: "Cannot mount volume. External hardrive."
date: 2010-02-15
forum: General Help
---

### Post by Johndo1 on 2010-02-15
Cannot mount volume.

Unable to mount the volume 'My Passport'.

Details

$MFTMirr does not match $MFT (record 0). Failed to mount '/dev/sdb1': Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.

I'm trying to reinstall ubuntu because I messed up a bunch of stuff but I need to back it up on this hard drive which won't mount in any linux distro.

Have any thoughts?

---

### Post by tom.swartz07 on 2010-02-15
> **Johndo1 said:**
> Cannot mount volume.

Unable to mount the volume 'My Passport'.

Details

$MFTMirr does not match $MFT (record 0). Failed to mount '/dev/sdb1': Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.

I'm trying to reinstall ubuntu because I messed up a bunch of stuff but I need to back it up on this hard drive which won't mount in any linux distro.

Have any thoughts?

Ive just finished reading this post:[http://ubuntuforums.org/showthread.php?t=1383882](http://ubuntuforums.org/showthread.php?t=1383882)

In particular, you should try this, from post #9: [http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities](http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities)

That seems to have cleared up many problems with a lot of people, its worth a shot for you too!

---

### Post by Johndo1 on 2010-02-17
didn't seem to work

---

### Post by jamesisin on 2010-02-17
Blow out the partition and format it to ext3/4 for this project?

---

### Post by Johndo1 on 2010-02-28
> **jamesisin said:**
> Blow out the partition and format it to ext3/4 for this project?

What do you mean? I've completed my original project but now I just wan't to get it to work. Should I reformat it?  

I've tried a bunch of stuff and nothing seems to be getting it to work.

Edit: I chkdsk /f in windows for a second time and it started working.

---

### Post by jamesisin on 2010-02-28
Yeah, I was suggesting removing all partitions and reformatting the entire drive.  Start from square one, as it were.  But it sounds as though you finally made progress.

---

