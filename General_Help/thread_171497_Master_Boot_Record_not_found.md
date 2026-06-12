---
title: "Master Boot Record not found"
date: 2006-05-06
forum: General Help
---

### Post by AusIV4 on 2006-05-06
Hi,
I recently built my own PC from parts I ordered online. I'm trying to install Ubuntu on the computer, but after installation, the computer acts as though there is still no operating system installed.

I've tried the Breezy Install CD and the Dapper install using the pretty installer. I've tried updating the master boot record using a live CD, but no matter what I try, the computer continues to act as if there is nothing installed on the hard drive.

I currently have two drives in the machine, and I've tried installing to both, and swiching which is hda and which is hdc.

In my current setup, hda is a 250 gb hard drive that was formatted before I started the installation process. hdb is a 120 gb hard drive that has an old Ubuntu installation on it, along with a large number of files I'd like to recover. I was a bit suprised that when this drive was hda, the system did not find the MBR from the past installation.

I don't know enough about how the computer loads the master boot record to do much more troubleshooting myself, so I'm hoping somebody can get me pointed in the right direct.

-Edit-
I might add that ultimately I'd like the 120 GB hard drive to be the drive I actually boot, and use the 250 GB for storage, but I'm not particularly concerned which drive has the MBR.

---

### Post by sinkxdie on 2006-05-06
Do you have a Windows Xp recovery disk? Did you try the recovery console in it and typing fixmbr?

---

### Post by AusIV4 on 2006-05-06
I don't believe I do have a windows XP recovery disk. Is there a free equivalent?

---

### Post by rcarring on 2006-05-06
It may be obvious, but have you checked if your mboard bios will support hard disks over 100GB? Source an old 10GB and try that first.

One otheridea I had was that the 250GB hard disk is all NTFS, and this may be a problem.

---

### Post by AusIV4 on 2006-05-07
The compile date for the BIOS is less than 6 months ago, so I can't imagine it wouldn't have support for large drives. I actually got the motherboard to replace one that would not recognize my 250 GB hard disk. On the old motherboard, the bios didn't recognize the existance of the 250 GB disk. On the new one, it recognizes it, and when I boot to linux using a live CD, it is able to give me detailed information about the drive, as well as mount the drive. I'll see if I can find anything about other people with the same motherboard having problems.

Also, where did you get the idea that the 250 GB disk is all NTFS? When I installed Ubuntu I had it format the drive into 3 partitions (Linux, Extended and swap), the large part of the drive is ext3.

---

### Post by AusIV4 on 2006-05-08
This morning I decided I would try to see if I could install on a smaller hard drive, so I pulled a 40 GB hard disk out of an older computer (this was the drive with the MBR for the other computer). When I put it in, it booted to my installation on the 250 GB hard drive. I didn't have to install anything, it just booted right away. I would rather not have to leave this drive in my computer because its needed elsewhere, but I'm going to see if I can't find a cheap, small hard drive to put the MBR (and possibly a few files) on.

---

