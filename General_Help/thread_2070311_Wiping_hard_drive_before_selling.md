---
title: "Wiping hard drive before selling"
date: 2012-10-12
forum: General Help
---

### Post by GammaPoint on 2012-10-12
Hi, I am selling one of my computers and would like to wipe the hard drive before selling. I found some instructions here:
[http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/](http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/)
using the wipe command. 

I just have one question. When I do 'sudo fdisk -l' to list the drives I see 3 drives (/dev/sdaX) where X=1,2,5. These drives correspond to 'Linux', 'Extended', and 'Linux swap /Solaris', respectively. The latter two correspond to about 2M blocks, whereas the Linux drive is much larger. When I wipe the drive, should I just do /dev/sda1, or should I do them all? 

Thanks!

---

### Post by plucky on 2012-10-12
> **GammaPoint said:**
> Hi, I am selling one of my computers and would like to wipe the hard drive before selling. I found some instructions here:
[http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/](http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/)
using the wipe command. 

I just have one question. When I do 'sudo fdisk -l' to list the drives I see 3 drives (/dev/sdaX) where X=1,2,5. These drives correspond to 'Linux', 'Extended', and 'Linux swap /Solaris', respectively. The latter two correspond to about 2M blocks, whereas the Linux drive is much larger. When I wipe the drive, should I just do /dev/sda1, or should I do them all? 

Thanks!

All your data will be on the sda1 partition,there should be nothing on the swap partition.You could run gparted and delete the swap and extended partitions.


Good Luck

---

### Post by GammaPoint on 2012-10-12
> **plucky said:**
> All your data will be on the sda1 partition,there should be nothing on the swap partition.You could run gparted and delete the swap and extended partitions.


Good Luck

Thanks plucky! Will do that.

---

### Post by cool110 on 2012-10-12
I would recommend using the ATA Secure Erase command on /dev/sda
[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

### Post by dcstar on 2012-10-13
> **cool110 said:**
> I would recommend using the ATA Secure Erase command on /dev/sda1
[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

+1

Anything else is basically hoping that someone doesn't have rudimentary data recovery skills.

---

### Post by Wim Sturkenboom on 2012-10-13
I wonder how far somebody with **rudimentary** recovery skills gets when one overwrites the disk with data from /dev/zero or /dev/random.

---

### Post by efflandt on 2012-10-13
I imagine if you used dd to write /dev/random to the entire drive (sda, not sda#) and then /dev/zero over that it would probably be difficult to impossible for someone to get any meaningful data from the drive even with special hardware.  But just writing /dev/zero to the entire drive would make it appear to be totally empty with no partitions to any OS or data recovery program.

---

