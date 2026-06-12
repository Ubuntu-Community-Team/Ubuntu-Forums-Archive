---
title: "Best filesystem configuration for hard drives of multiple sizes"
date: 2012-04-17
forum: General Help
---

### Post by ttshivers on 2012-04-17
I was just wondering what the best file system and configuration for an array I want to build. I have 2 (2 TB) hard drives and 2 (500 gb) hard drives. I would like to have the most storage space available but also 1 level of redundancy. I would like to have 2 copies of a file on two different drives. This configuration would allow me 2.5 TB of usable storage space. Would a mirrored btrfs configuration be the best or is there another option?

---

### Post by sj1410 on 2012-04-18
RAID1 is the only option if you need redundancy. If you could add 1 500GB and 1 2TB harddisk, than RAID5 would have give you redundancy, with performance and more available space (5TB).

btrfs is evolving but not stable yet, I still prefer ext4.


for creating raid refer to 

[http://www.techpage3.com/2011/01/simple-recipe-to-create-raid5-under.html](http://www.techpage3.com/2011/01/simple-recipe-to-create-raid5-under.html)

---

### Post by strask on 2012-04-18
> **sj1410 said:**
> RAID0 is the only option if you need redundancy.

You mean RAID1. :)

---

### Post by sj1410 on 2012-04-18
:D yeah RAID1 is mirroring.

---

### Post by dcstar on 2012-04-18
> **strask said:**
> You mean RAID1. :)

Yep, RAID 0 is the exact opposite of "Redundancy", it is totally evil and does not deserve to have a "RAID" designation.

With Striping ("RAID 0") you double the statistical chances of drive failure and you lose **all** your data if one drive of the pair fails.

---

### Post by ttshivers on 2012-04-18
Actually, RAID5 with your proposed additional drives would only give me 2.5TB of usable space, since RAID5 usable space can be modeled by this equation:

(n-1) *s
where n is the number of drives and s is the smallest drive in the array.
In my case this is what happens since I have a 500GB drive.
(6-1)*500GB = 2500GB or 2.5 TB

I want to be able to use the available disks I have and not buy any others.

I am looking for a way to create a redundant disk pool which can accommodate multiple drive sizes. Now from what I understand about btrfs mirroring, it makes sure that a file is present on 2 separate disks in the array, which is probably the best solution for me. Since it would half my total array size and give me a total array size of 2.5TB. Is there a better and more stable way of doing this, since btrfs is still experimental?

---

### Post by sj1410 on 2012-04-19
2TB x (3-1) = 4TB Usable space
500GB x (3-1) = 1TB Usable Space

Total 5TB Usable Space

---

### Post by ttshivers on 2012-04-21
This would create 2 different volumes unless you suggest combing them with something with lvm.

---

### Post by Ceiber Boy on 2012-04-21
> **dcstar said:**
> Yep, RAID 0 is the exact opposite of "Redundancy", it is totally evil and does not deserve to have a "RAID" designation.

With Striping ("RAID 0") you double the statistical chances of drive failure and you lose **all** your data if one drive of the pair fails.
Yep, but its FAST! as long as you understand the risk and are willing to except the consequences RAID0 is fine! I always (if allowed by my employers) configure my work machines as RAID0 for the performance benefits, in that cerario we have an extensive backup strategy negating the risk of the configuration.

---

### Post by jmate24 on 2012-06-22
yes i personally would go with lvm in that senario but to remember to put a separate /boot partition at the front of the first drive or you will be unable to boot and if you have a usb hard drive then I would suggest using it with deja-dup. Or ordering online backup with [http://one.ubuntu.com]("http://one.ubuntu.com") and deja-dup can backup to the web.

best of luck.

---

