---
title: "HDD to SSD Transition"
date: 2011-07-06
forum: General Help
---

### Post by Fightback on 2011-07-06
Hi Guys.

I am currently on a (per Wubi installed) dual-booted machine with Ubuntu (11.04) and Win 7 64-bit.
I only have a HDD installed at the moment, but I would like to install a SSD and boot both my Ubuntu and my Windows from it (for the speed).
First of all: Does it make sense to spend money on a SSD? I am really only thinking about buying one since I have read and seen the quite impressive speed with which an OS boots on a SSD.

Also, I was wondering how a smooth transition from HDD to SDD could be accomplished. I am aware of the fact that I will have to reinstall both Ubuntu and Windows on the SSD, that's not that much of a problem as it is only a time-consuming task.
I have a complete backup from my home folder of Ubuntu (Duplicity) and a Windows backup made with the tool that comes with Windows 7 on a NAS. Now, my second question is, which things should be placed on the SSD (which is not going to be larger than 128 GB) for a good performance?

Given I decide to buy a SSD; which one should I buy? I have an Asus P5Q-PRO Mainboard, an Intel Quadcore Q8200 "Yorkfield" with 2.33 GHz, 8GB of Mushkin RAM and a Radeon HD 4870 with 1GB. As said above, the drive should be be either 64 GB or 128 GB and it shouldn't cost more than about 150$ (or CHF, since I live in Switzerland, but at the moment, the dollar is actually worth less =])
I have seen that there are SSDs with SATA3 and that my Motherboard only supports SATA2, is that going to cause my any trouble if I buy a SATA3 SSD or is it backwards-compatible?
And finally, are there any tips for me that prevent me from doing other stupid mistakes?

---

### Post by seawolf167 on 2011-07-06
> **Fightback said:**
> First of all: Does it make sense to spend money on a SSD? I am really only thinking about buying one since I have read and seen the quite impressive speed with which an OS boots on a SSD.

If you don't have the money it doesn't make sense, but if you do have the money, there is a **very** nice and noticable speed boost, enough so you won't ever want to go back to a disk drive for your boot system ever again.

> **Fightback said:**
> Also, I was wondering how a smooth transition from HDD to SDD could be accomplished. I am aware of the fact that I will have to reinstall both Ubuntu and Windows on the SSD, that's not that much of a problem as it is only a time-consuming task.

I suggest resizing your current hard drive partitions so they are less than the size of your new SSD, then cloning the partitions with [Clonezilla]("http://www.clonezilla.org"). You can then restore the partitions to your new SSD, and all you will have to worry about is your MBR and partition boot records, which are easy to reinstall. This way you don't have to re-setup anything on your computer.

> **Fightback said:**
> I have a complete backup from my home folder of Ubuntu (Duplicity) and a Windows backup made with the tool that comes with Windows 7 on a NAS. Now, my second question is, which things should be placed on the SSD (which is not going to be larger than 128 GB) for a good performance?

SSDs cost *a lot* more per GB of storage than traditional disk drives. As a general rule of thumb, place only boot, root, and commonly accessed programs on your SSD, place everything else (music, videos, documents, backups, etc.) on traditional disk drive media.

> **Fightback said:**
> Given I decide to buy a SSD; which one should I buy? I have an Asus P5Q-PRO Mainboard, an Intel Quadcore Q8200 "Yorkfield" with 2.33 GHz, 8GB of Mushkin RAM and a Radeon HD 4870 with 1GB. As said above, the drive should be be either 64 GB or 128 GB and it shouldn't cost more than about 150$ (or CHF, since I live in Switzerland, but at the moment, the dollar is actually worth less =])

Can't really help you here, I only have a couple of [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820148348").

> **Fightback said:**
> I have seen that there are SSDs with SATA3 and that my Motherboard only supports SATA2, is that going to cause my any trouble if I buy a SATA3 SSD or is it backwards-compatible?

They are backwards-compatible, but you will not recieve full speed if you are plugged into an older SATA port. I suggest getting a SATA II if you have no plans to upgrade your motherboard.

> **Fightback said:**
> And finally, are there any tips for me that prevent me from doing other stupid mistakes?

Research, read, research more, read more... lol

---

