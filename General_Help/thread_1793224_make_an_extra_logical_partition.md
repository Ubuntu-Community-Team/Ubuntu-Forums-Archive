---
title: "make an extra logical partition?"
date: 2011-06-29
forum: General Help
---

### Post by blackbird34 on 2011-06-29
Hi 
is it possible? I have four partitions already, /dev/sda4 is logical:

/dev/sda1: 
/dev/sda2:
/dev/sda3: 
/dev/sda4 ==>/dev/sda5: swap
                ==>/dev/sda6: empty

So is it possible to turn sda2 into a logical one? what filesystem type do you choose on gparted? the whole problem comes from sda4 being to small for what i want to do and sda3 being windows:popcorn:, which i don't really want to move in case it's wrecked

---

### Post by coffeecat on 2011-06-29
> **blackbird34 said:**
> I have four partitions already, /dev/sda4 is logical:

No, from the layout you have posted, sda4 is the extended partition. An extended partition acts as a container for logical partitions. Logical partitions are numbered 5 and upwards, so your sda5 and sda6 will be logicals inside the sda4 extended partition. The only way of using the space occupied by sda2 as a logical partition is if it is adjacent to the extended partition. Then you would be able to delete sda2 and enlarge the extended partition into the freed space and make a new logical. However, it sounds as though sda3 is in the way.

Post a screenshot of the Gparted window so that we can see exactly what is going on. Also - what version of Windows do you have?

---

### Post by blackbird34 on 2011-06-29
Yeah, sda3 is in the way, thats the problem. It's Windows 7. And i don't dare move it...[-X

---

### Post by coffeecat on 2011-06-29
> **blackbird34 said:**
>  It's Windows 7. And i don't dare move it...[-X

I sympathise with your caution. But Windows 7 in a 24GiB partition? Did you have to get it to breathe in when you installed it? :wink:

Your options are limited. I can see two possibilities:

1 - Backup your personal data from Ubuntu and use the live CD to delete sda5, sda6 and sda4. Now delete sda2 and create an extended partition in the 138GiB space. Create your logical partitions in that and re-install Ubuntu in those. Now create a primary partition in the 17 GiB released by the old sda4,5,6.***

2 - This does involve moving Windows, but not with Gparted. Attempting to move the Windows partition with Gparted would probably end in making Windows unbootable, because you would be moving the start sector and this is what really upsets Windows. However, Windows 7 comes with its own Disk Management utility with which you can manipulate the Windows C: partition with (relative) safety. I can't remember whether you can move a partition with it, but if not simply use Windows' Disk Management to move the partition in a 2-step process. First, enlarge the partition backwards into the 138GiB space. Then shrink it by moving the right boundary. Having said all that, Windows will probably leave some stuff up at the right end of the partition and refuse to allow you to shrink it by the amount you want. There are ways around that, but it's still a gamble whether you would be able to shrink it back to about 24GiB.

Good luck!

*** **EDIT**: I just noticed that your Ubuntu root partition was sda1. This makes deleting sda4,5,6 and creating an extended partition in place of sda2 viable without having to reinstall Ubuntu. What is sda6? You'd have to take precautions around making a new swap partition, but this is doable.

---

### Post by blackbird34 on 2011-06-29
I think i'll follow the edit :D

I removed ALL the junkware from windows and it is rather lean and fast. I don't use it much. 
I've put a new screenshot of what i plan to do on gparted and am about to go ahead. But what filesystem type do i format /dev/sda3 to to get an container for logical partitions? /dev/sda4 used to say it was "extended" but that option doesn't show up...

---

### Post by coffeecat on 2011-06-29
I see you have enlarged your Windows partition. I thought you didn't dare mess with it. [-X  :wink:

Anyway - your 138.35 partition. You don't format extended partitions. You need to delete the 138.35GiB primary partition and in the freed space create an extended partition first. Partition > New > Create as: extended partition. Apply that and then you will be able to make your logical partitions (as many as you need) in the unallocated space that will show within the extended.

**EDIT**: STOP! :)

I see you are about to enlarge the Windows partition in Gparted. It is much safer to use Windows' own Disk Management for this. Do what you can in Gparted and then use Windows for enlarging the Windows C: partition.

---

### Post by nzjethro on 2011-06-29
When you create your partition in your unallocated space, using Gparted there should be an option to "Create as" with a dropdown menu.

---

### Post by blackbird34 on 2011-06-29
There we go.
Off to windows. Hope this helps someone. Thanks everybody.

---

