---
title: "Help with disk structure."
date: 2012-09-04
forum: General Help
---

### Post by area1509 on 2012-09-04
I have searched for the answer to this question and all I come up with is the directory structure of the root drive (/).

What I am looking for is an explanation of the drive structure, my first hard drive is sda and has sda1 and sda5 what are these and do they need to be mapped?

also what happened to sda2, sda3, sda4, is there a sda0 and what are these used for?
thanks for your help. A.J. (newby)

---

### Post by Kopkins on 2012-09-04
Those are partitions. The hard disk in the first drive is referred to as sda. This is the disk as a whole. When you do things like add different operating systems (like Ubuntu) or want to have separate sections for different types of files, partitions come into play. The numbering starts at 1 for the first partition. This will be sda1. To refer to the fifth partition it would be sda5. 

You can have more than one disk, for example, if you plug in a usb drive you'll have another disk. the last letter changes in the name. It changes from sda to sdb. So the name is sdb and the partitions are sdb1, sdb2, and so forth.

In your case, what I suspect is happening with your numbering is related to the type of partitions. A disk can have up to four primary partitions. After the four primary partitions are used, it must move onto logical partitions. A logical partition holds more partitions called extended partitions. I think that you have a primary partition at sda1 and an extended partition at sda5. 

If you post up your disk configuration we can give you more information. A good way to do this is to use gparted. If you haven't installed it, enter the code in a terminal. ```
sudo apt-get install gparted
```
Then open up the dash (if using 12.04) and type gparted and press enter. It will automatically scan and load information about your primary disk. Take a screenshot and upload it if you would like. 

Kopkins

---

### Post by area1509 on 2012-09-04
Ok what are sda2 and sda5 used for and should they be mapped? say to my home folder?

---

### Post by LiamOS on 2012-09-04
From the above image, it seems that your entire system is on one partition.
sda2 is an extended partition, which means that it can contain extra partitions, and sda5 is a swap partition within this. 
If you're unsure what swap is, see here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

sda3 and sda4 do not seem to exist on this system.

---

### Post by doktorOblivion on 2012-09-04
This may help as well, a discussion on dual booting, which when performing you must take into account these issues.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by dandnsmith on 2012-09-04
Just on more bit of info about partition numbering:
Whatever the number is of the extended partition, the first logical partition within it will be sda5 (or equivalent for other HDDs) by convention - it doesn't have to be, but always happens that way.

---

### Post by area1509 on 2012-09-04
Ok so thats where I was confused is disk1\part1\ext-part5\
so I could have a part2\ext-part5..6..7..8 and disk1\part2..3..4 do not exist.

that makes sense well to me at least.
and the swap is just used by the system as extra memory IE fake RAM.
correct?

---

### Post by Kopkins on 2012-09-04
> **area1509 said:**
> Ok so thats where I was confused is disk1\part1\ext-part5\
so I could have a part2\ext-part5..6..7..8 and disk1\part2..3..4 do not exist.

that makes sense well to me at least.
and the swap is just used by the system as extra memory IE fake RAM.
correct?

Yes. Although, from your screenshot it looks like your swap is not in use. So your system can't access it. To check if it is in use, open the dash and type system monitor, then go to the resources tab. Halfway down on the right should be an indication of your swap. 

Or do ```
sudo swapon /dev/sda5 
```

And if you get a message saying you can't because it is busy, then your swap is active, If you don't, then it just mounts your swap partition. 

Kopkins

---

### Post by area1509 on 2012-09-04
Cool I learn somthing new every day...
Thank you guy's so much.

---

### Post by Bachstelze on 2012-09-04
> **Kopkins said:**
> 
In your case, what I suspect is happening with your numbering is related to the type of partitions. A disk can have up to four primary partitions. After the four primary partitions are used, it must move onto logical partitions. A logical partition holds more partitions called extended partitions. I think that you have a primary partition at sda1 and an extended partition at sda5. 

A (MBR-style) disk may have up to four partitions, always. It can be either four primary partitions, or three primary paritition plus one extended partition. An extended partition in turn can contain as many logical partitions as one wishes. Here, sda2 is an extended partition, that contains the logical partition sda5.

*EDIT:* Of course you can have an extended partition with less than three primary partitions, as is the case here. The point is that the extended partition takes one of the four "slots", it doesn't come in addition to them.

---

### Post by Kopkins on 2012-09-04
Thank you for the correction. I didn't reference anything and haven't dealt with disk layout in a while. 

Kopkins

---

