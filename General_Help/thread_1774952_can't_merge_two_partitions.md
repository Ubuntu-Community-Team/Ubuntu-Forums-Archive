---
title: "can't merge two partitions"
date: 2011-06-04
forum: General Help
---

### Post by cybo on 2011-06-04
i used to have 2 partitions: ubuntu and windows. i removed windows and currently am trying to merge it into ubuntu using GParted. however for some reason Gparted won't allow me to increase the size of my ubuntu partition. if you look at the picture that is attached, i need to merge /dev/sda2 and /dev/sda5 . does anybody know why i can't merge them or if there is other software i can you for it?

any help is appreciated.

thanks

---

### Post by atomizer on 2011-06-04
sda2 is a primary partition and sda5 is an extended partition.


you cannot merge those 2

---

### Post by -kg- on 2011-06-04
> **atomizer said:**
> sda2 is a primary partition and sda5 is an extended partition.


you cannot merge those 2

No, sda5 is not an extended partition.  sda5 is a logical partition which is contained within an extended partition, which is sda4.  Look at the partitions list below the graphics.

According to Gparted, you have approximately 2 GB of data on sda2, with 11 GB free on sda5.  Copy whatever critical data you have on sda2 to sda5.  Then delete sda2.  That will give you that space as unallocated space.  If you anticipate not needing sda1 (it is a Windows "boot" partition formatted to NTFS...you won't really need it), then delete that as well for the extra space (the GRUB bootloader is contained in the first part of the hard drive extraneous to any partition).

The next thing you will need to do is expand sda4 (the Extended partition) into that unallocated space.  Then you will need to expand sda5 into the space created by the expansion of the Extended partition.  You should be in like flint from that point.

For a better understanding of what you're doing, read at the link in my signature block.  Gparted doesn't support merging two partitions, and in any case, you can't merge partitions over the boundary of an Extended partition.

---

### Post by cybo on 2011-06-04
i deleted sda2 but it won't let me expand sda4. it won't let me to expand sda4. is there a way to set sda4 to primary?

---

### Post by cybo on 2011-06-04
what if i create an image of my linux parition, delete the linux parition, merge sda2 and sda4 and put an image onto the newly created parition. is it possible? i have an old harddrive which i connect through a ide to usb connector to my laptop. would it be possible to put an image on it and then move it back to a newly created partition? what toold will i need to achive this?

any help is appreciated.

---

### Post by desnaike on 2011-06-04
Maybe the swap partition in between the two is the problem.

---

### Post by coffeecat on 2011-06-04
You cannot resize sda4 while you are running Ubuntu from sda5. While any logical partition is in use, its extended partition is effectively locked. You need to use Gparted from the live CD to be able to resize sda4. When you open the live CD Gparted, you will find sda4 locked at first - the key symbol. This is because the live session has activated your sda6 swap partition. Right-click on sda6 and choose "swapoff". Then you will be able to resize sda4.

---

### Post by cybo on 2011-06-04
> **desnaike said:**
> Maybe the swap partition in between the two is the problem.

so how would i fix it?

---

### Post by cybo on 2011-06-08
thanks. it worked. now i still have a few issues. there are two sections of unallocated space, totalling 7.38 MiB. for some reason i'm not able to merge them into existing partitions. i tried running the same procedure coffeecat recommended but for some reason everything stays the same. what might be the reason for that and how would i go about fixing it?

any help is appreciated,
thanks

---

### Post by coffeecat on 2011-06-08
It could be to something to do with sector boundaries, but to be honest, I would leave things as they are anyway. About 7MB unused in a 150GB drive is negligible. You'd have to try to enlarge both the extended partition and then the ext4 sda5 partition to recapture that space. The main issue would be that you would be enlarging the sda5 partition to the left rather than to the right, which always takes much longer. Add to this the risk that is always incurred when manipulating partitions, I would suggest leaving things as they are.

I know it's irritating having that unused space hanging around. Best thing is not to look in Gparted too often! :)

---

