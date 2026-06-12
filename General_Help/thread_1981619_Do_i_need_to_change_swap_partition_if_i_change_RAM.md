---
title: "Do i need to change swap partition if i change RAM"
date: 2012-05-17
forum: General Help
---

### Post by soumoks on 2012-05-17
Hey guys i read that the size of swap partition depends on the amount of RAM installed in the system,so was wondering whether one has to change the size of this partition if i change RAM i.e increase RAM,i currently have 2 gigs and am planning to upgrade to 4 gigs,so do i have to change the size of the swap partition?

---

### Post by evilsoup on 2012-05-17
If you use hibernate, yes. Otherwise, no.

---

### Post by prshah on 2012-05-17
> **soumoks said:**
> Hey guys i read that the size of swap partition depends on the amount of RAM installed in the system,so was wondering whether one has to change the size of this partition if i change RAM i.e increase RAM,i currently have 2 gigs and am planning to upgrade to 4 gigs,so do i have to change the size of the swap partition?

The swap partition is used to store hibernation information when and if you hibernate.

Because of this, it is better to have a swap partition that is (approx) 1.1 * RAM (10% more than installed RAM).

However, if you do not use hibernation, or already have a suitably sized swap partition, then you need not make any changes.

To change the swap partition, it is better that you use gparted from a live CD to extend the partition size, rather than create a new partition altogether. 

Please post back if you need further information.

---

### Post by soumoks on 2012-05-17
> **prshah said:**
> The swap partition is used to store hibernation information when and if you hibernate.

Because of this, it is better to have a swap partition that is (approx) 1.1 * RAM (10% more than installed RAM).

However, if you do not use hibernation, or already have a suitably sized swap partition, then you need not make any changes.

To change the swap partition, it is better that you use gparted from a live CD to extend the partition size, rather than create a new partition altogether. 

Please post back if you need further information.
my RAM is 2 gig and the swap partition is also the same and i don't use hibernation a lot,it does not matter whether i change the swap partition or not when i increase my RAM right?

---

### Post by prshah on 2012-05-17
> **soumoks said:**
> my RAM is 2 gig and the swap partition is also the same and i don't use hibernation a lot,it does not matter whether i change the swap partition or not when i increase my RAM right?


No, you do not need to change your swap partition to increase your RAM. Your system will automatically recognize and use increased RAM without any action on your part.

However, the next time you plan to use hibernate, it will fail until you increase swap size.

---

### Post by idoitprone on 2012-05-17
> **prshah said:**
> No, you do not need to change your swap partition to increase your RAM. Your system will automatically recognize and use increased RAM without any action on your part.

However, the next time you plan to use hibernate, it will fail until you increase swap size.

No need to repartition to increase swap. Just make a  Swap file [https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)

---

### Post by soumoks on 2012-05-17
> **prshah said:**
> No, you do not need to change your swap partition to increase your RAM. Your system will automatically recognize and use increased RAM without any action on your part.

However, the next time you plan to use hibernate, it will fail until you increase swap size.
thanks will try that out when i change my RAM..

---

### Post by soumoks on 2012-05-17
> **idoitprone said:**
> No need to repartition to increase swap. Just make a  Swap file [https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)
thanks..

---

### Post by kurt18947 on 2012-05-17
> **idoitprone said:**
> No need to repartition to increase swap. Just make a  Swap file [https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)

Swap files can't be used for hibernation/suspend-to-disk.  Swap files work fine to extend RAM.  I haven't created swap partitions but have created swap files.  But I use suspend (to RAM) not Hibernate (suspend-to-disk).  Actually I'll retract that statement.  I have an old notebook with 512 MB. RAM.  That machine has a swap partition and it gets used.  Other machines with 2+ GB. RAM don't have swap partitions or swap files and seldom use more than 1 GB. RAM for my uses.

---

### Post by idoitprone on 2012-05-17
> **kurt18947 said:**
> Swap files can't be used for hibernation/suspend-to-disk.  Swap files work fine to extend RAM.  I haven't created swap partitions but have created swap files.  But I use suspend (to RAM) not Hibernate (suspend-to-disk).  Actually I'll retract that statement.  I have an old notebook with 512 MB. RAM.  That machine has a swap partition and it gets used.  Other machines with 2+ GB. RAM don't have swap partitions or swap files and seldom use more than 1 GB. RAM for my uses.

It is possible to hibernate with swap file
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
You have to jump through hoops thou

---

### Post by kurt18947 on 2012-05-17
> **idoitprone said:**
> It is possible to hibernate with swap file
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
You have to jump through hoops thou

I did not know that,  thanks.  I think I'd create a swap partition if I wanted hibernation though.  "Jumping through hoops" is right.

---

### Post by idoitprone on 2012-05-17
> **kurt18947 said:**
> I did not know that,  thanks.  I think I'd create a swap partition if I wanted hibernation though.  "Jumping through hoops" is right.

well if you start acpi... I rather stab myself with a knife than maintain software using the acpi interface.

---

