---
title: "URGENT :: Recover Unallocated HardDisk ??"
date: 2011-06-11
forum: General Help
---

### Post by vaibhav.dkm on 2011-06-11
I am right now using ubuntu Live CD to boot and post this thread .. 
My attachment no 1 show you the result of 

> sudo fdisk -luMy Other Attachment is of Gparted Screenshot..
Can I Recover my Data anyhow ?? Plz help... it's really important 

Using Ubuntu 10.10 ..

---

### Post by YesWeCan on 2011-06-11
What did you do to cause this?

---

### Post by vaibhav.dkm on 2011-06-11
I was trying to increase my ubuntu space using Gparted but somehow i clicked somewhere wrong , i was able to use it properly that session but when i restart my computer , everything is plain chit .. 
HELP !!!

---

### Post by YesWeCan on 2011-06-11
You probably accidentally erased the partition table. This is like the table of contents of a book. So the data may still be there but the partitions are not identifiable.

I am not expert in recovering data when the partition table is missing. It may be possible in theory.

What partitions did/does the disk have on it? Have you any record of what they should be?

Would you post the output of:
sudo dd if=/dev/sda bs=512 count=1 | hexdump -C

Put it in code delimiters (use #)

---

### Post by coffeecat on 2011-06-11
This sounds like a job for testdisk. Testdisk scans the HD and can reconstruct the partition table on the basis of the filesystems and other data it finds. You can install testdisk to the live CD session and run it from there. Useful link:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

**EDIT**: don't run photorec (yet) which comes with testdisk. Testdisk is for rescuing partitions by reconstructing the partition table. Photorec is for retrieving files from corrupted or reformatted drives/partitions.

---

### Post by westie457 on 2011-06-11
Good call 'coffeecat'.

I was going to suggest using Gparted from an Ubuntu LiveCD with information from this link

[http://www.mohdshakir.net/2008/01/03/recover-lost-partition-table-using-ubuntu-live-cd-gpart]("http://www.mohdshakir.net/2008/01/03/recover-lost-partition-table-using-ubuntu-live-cd-gpart")

---

### Post by YesWeCan on 2011-06-11
> **coffeecat said:**
> This sounds like a job for testdisk. Testdisk scans the HD and can reconstruct the partition table on the basis of the filesystems and other data it finds.
Very good. :)

---

### Post by coffeecat on 2011-06-11
> **YesWeCan said:**
> Very good. :)

It is! I once had to use testdisk when I accidentally typed /dev/sda in the terminal when wanting to zero out sdc. I quickly ctrl-C'd the shred command but not before the partition table on sda has been wiped. :redface: Testdisk came to the rescue and I soon had my partition table back.

---

### Post by YesWeCan on 2011-06-11
> **coffeecat said:**
> It is! I once had to use testdisk when I accidentally typed /dev/sda in the terminal when wanting to zero out sdc. I quickly ctrl-C'd the shred command but not before the partition table on sda has been wiped. :redface: Testdisk came to the rescue and I soon had my partition table back.
Phew! or what? Not bad, eight lives left. ;)

---

### Post by vaibhav.dkm on 2011-06-11
thanks , i trying the solution :)

---

