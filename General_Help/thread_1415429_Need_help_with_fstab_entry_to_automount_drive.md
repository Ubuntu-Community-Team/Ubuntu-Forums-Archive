---
title: "Need help with fstab entry to automount drive"
date: 2010-02-24
forum: General Help
---

### Post by cforput on 2010-02-24
Using Karmic. 

I have a single physical drive with 3 logical drives on it (actually more but it is insignificant to my question). I put the following line in my fstab file:

 /dev/sda5 /media/SHAREDDRIVE vfat auto  auto,user,exec,rw  0  2

Here is the output from sudo blkid
/dev/sda1: UUID="58C0B119C0B0FE76" LABEL="System" TYPE="ntfs" 
/dev/sda2: UUID="01CAB14019104380" LABEL="TI105756W0B" TYPE="ntfs" 
/dev/sda4: UUID="A4FAFCC7FAFC9730" LABEL="HDDRECOVERY" TYPE="ntfs" 
/dev/sda5: LABEL="SHAREDDRIVE" UUID="57B4-F680" TYPE="vfat" 
/dev/sda6: UUID="9388fbea-1311-499f-9a42-27c2bfda569a" TYPE="ext4" 
/dev/sda7: UUID="a404172d-87aa-4f65-a953-8f64c3c154f4" TYPE="swap" 


This isn't working for 2 reasons. 
1) I am suppose to create a blank folder - /media/SHAREDDRIVE. If I do that, then, since the volume label for the drive is SHAREDDRIVE a drive mounts as SHAREDDRIVE but all my files are actually in SHAREDDRIVE_. I have some scripts that point to SHAREDDRIVE so they are trying to access the wrong folder. Thunderbird is also looking for files on SHAREDDRIVE so none of my e-mails come up.
2) I can't unmount SHAREDDRIVE. I get an error message saying I am not root so it seems like my parameters are not correct in my fstab file. 

I need to know 2 things: 
1) What are the correct options to use for what I am trying to do.
2) How do I handle the blank folder under /media where I seem to have some type of conflict with both the drive's volume label and the mount name the same?

---

### Post by zvacet on 2010-02-25
Read [this.]("http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm")

---

### Post by cforput on 2010-02-25
This worked perfectly! Thanks

---

