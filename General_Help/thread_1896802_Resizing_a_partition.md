---
title: "Resizing a partition"
date: 2011-12-17
forum: General Help
---

### Post by rmcellig on 2011-12-17
I want to resize sda5 all the way to the left and then  create a swap file from what remains to the right. How can I do this?

---

### Post by tears of the river on 2011-12-17
> **rmcellig said:**
> I want to resize sda5 all the way to the left and then  create a swap file from what remains to the right. How can I do this?

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

i believe this should help just go through it carefully

:D

---

### Post by wildmanne39 on 2011-12-17
Hi, here is a link that explains about resizing partitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
Thanks

---

### Post by bluexrider on 2011-12-17
> **rmcellig said:**
> I want to resize sda5 all the way to the left and then  create a swap file from what remains to the right. How can I do this?
???????? huh! Why would you create a 90+GB swap. am I missing something or did I read it wrong

---

### Post by bluexrider on 2011-12-17
Oh and YOU CAN'T if you are mounted and booting from that partition, Which it looks like you may be doing.

---

### Post by rmcellig on 2011-12-18
> **bluexrider said:**
> Oh and YOU CAN'T if you are mounted and booting from that partition, Which it looks like you may be doing.

I booted from the ubuntu 11.04 live cd and am using Gparted from the live cd. I have all this unallocated space to the left of sda5. I want to extend sda5 to the left to take up all the unallocated space. To the right of sda5 you will see that i have a small amount of unallocated space that I can use for the swap file.

When I go to resize sda5, the resize window does not show me the unallocated space that ivwant to extend sda5 to. My question is why.

---

### Post by bluexrider on 2011-12-18
> **rmcellig said:**
> I booted from the ubuntu 11.04 live cd and am using Gparted from the live cd. I have all this unallocated space to the left of sda5. I want to extend sda5 to the left to take up all the unallocated space. To the right of sda5 you will see that i have a small amount of unallocated space that I can use for the swap file.

When I go to resize sda5, the resize window does not show me the unallocated space that ivwant to extend sda5 to. My question is why.
It's an extended partition

[http://www.howtoforge.com/partitioning_with_gparted_p2](http://www.howtoforge.com/partitioning_with_gparted_p2)

this is a good example of how to move a partition without loosing data

---

### Post by rmcellig on 2011-12-18
Maybe what I will do is clone the partition to another drive using Clonezilla and then restore the clone to a fully reformatted drive. This should work? This is my test machine after all.

---

### Post by bluexrider on 2011-12-18
> **rmcellig said:**
> Maybe what I will do is clone the partition to another drive using Clonezilla and then restore the clone to a fully reformatted drive. This should work? This is my test machine after all.
that would be a good solution. then you could resize and format to what ever you wanted.

---

### Post by wildmanne39 on 2011-12-18
Hi, I do not know if cloning will work, I recently used clonzilla and it cloned my partitions exactly as they were on the other drive, I am not sure if that setting can be manually changed or not.

Also you should read the link I gave you in my previous post it explains the dangers and the ways that a partition can be resized.
Thanks

---

### Post by Synoc on 2011-12-18
all clonexilla does is ask you how to use dd without telling you you are using dd. if you ask it clone a partition... it will clone, JUST that partition. but I think you will have to create the new partitions on the drive before reimaging or it will use the entire drive left over as the partition. 

```
 dd if=/dev/sda1 of=loc/of/backup/media/sda1.bck
```
might work better the sda1 assumes you are infact backing up sda1. do this inserting the drive and partition names for each, then you can use dd to reimage the partitions by reversing the values of if= and of= (after you get the partitions where you want them. 

Keep in mind, dd and therefore clonzilla will make a bit-for-bit copy, so if you have a 300 GB partition it will be a 300 GB image.

---

### Post by Mark Phelps on 2011-12-18
> **Synoc said:**
> Keep in mind, dd and therefore clonzilla will make a bit-for-bit copy, so if you have a 300 GB partition it will be a 300 GB image.

Don't know about DD, but Clonezilla will only do that if you do a sector-based clone.  If you simply image off the partition and restore it, it saves only the used sectors.  So, unless the partition is 100% used, the resulting image will be smaller.

Also, when you use Clonezilla to write to a new drive, the resulting partition is the same size as the original -- not the entire space on the drive.

---

### Post by VanR on 2011-12-18
Make sure your swap partition is not mounted. Live CD will mount swap by default. All partitions must be unmounted.

---

### Post by rmcellig on 2011-12-18
I am at present cloning the partition (about 98GB) with about 17GB already taken with files etc... using Clonezilla to an external USB drive. After that I will reformat the Dell drive and restore the image to it as well as use Disk Repair (love this utility), to recreate the bootloader so it starts up properly. I have to do this because when I was moving around partitions in Gparted, the bootloader got nuked which was to be expected.

---

### Post by rmcellig on 2011-12-18
I did it!! and i learned  a lot along the  way. I cloned my HD partition, erased the drive, created a 100GB partition and recovered the cloned image to the  new100GB partition. I then extended the 100GB partition to take up the rest of my drive leaving 9GB to create a swap file. Clonezilla was pretty easy to use, i now  have Linux on my full HD like nothing ever happened. Love it!! 

Thanks for all your help and suggestions. I learned a ton from this exercise!!

---

### Post by tears of the river on 2011-12-18
Could you please mark the thread as solved if your problem is done
thank you
:)

---

### Post by bluexrider on 2011-12-19
Clonezilla did it for you. Perfect!

---

