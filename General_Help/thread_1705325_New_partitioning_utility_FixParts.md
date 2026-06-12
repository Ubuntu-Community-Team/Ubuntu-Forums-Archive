---
title: "New partitioning utility: FixParts"
date: 2011-03-12
forum: General Help
---

### Post by srs5694 on 2011-03-12
Hello all,

I've just officially released a new open source partitioning utility: [FixParts.]("http://www.rodsbooks.com/fixparts/") As the name implies, its purpose is to fix broken partition tables, although it also has a few other specialized uses. Broken partition tables often manifest in GParted and other libparted-based tools as an empty disk, even when you know partitions exist on it; or sometimes as a disk with incorrect partitions shown. FixParts' three main goals are:


[LIST]
[*]To remove stray GUID Partition Table (GPT) data from MBR disks. This problem can result from re-using a GPT disk by repartitioning it with a GPT-unaware utility, such as Linux fdisk or at least some versions of the Windows installer.
[*]To resize extended partitions that are too large or too small. This problem can be created by TestDisk under some circumstances, and perhaps by other tools, too.
[*]To change primary partitions into logical partitions, or vice-versa. Such changes might not technically be fixes of problems, but they can be, if something turned a logical partition into a primary partition, as the Windows XP installer does sometimes. This feature of the program can also be helpful in working around the problem of computer manufacturers who place four primary partitions on their disks at the factory.
[/LIST]


The program is *not* intended for general-purpose partitioning; for that, use fdisk, GNU Parted, GParted, Disk Utility, or other tools. You should also be aware that FixParts may change partition numbers. This shouldn't affect a typical Ubuntu installation, but it might if you use partition device filenames rather than UUIDs in /etc/fstab or your GRUB 2 configuration.

FixParts is an offshoot of my [GPT fdisk (gdisk and sgdisk)]("http://www.rodsbooks.com/gdisk/") package, which is used to partition GPT disks. Because FixParts has such different uses, though, I've put it into a separate binary package. You can download them all from the GPT fdisk [SourceForge download page.]("https://sourceforge.net/projects/gptfdisk/files/")

Many thanks to my alpha testers, including this forum's Rubi1200, Quackers, and coffeecat, who bravely offered their hard disks up as guinea pigs for the new software!

---

### Post by Rubi1200 on 2011-03-12
This is great news and will surely prove useful in various scenarios.

Thanks for sharing this with us.

---

### Post by Quackers on 2011-03-12
I can see the primarys to logicals being used :-)
Nice one!

---

### Post by coffeecat on 2011-03-12
It was fun testing this. I shall no doubt be suggesting use of this in due course. Partition tables left bruised and bleeding by the Windows installer seem to be happening with monotonous regularity and this is going to be an excellent tool for dealing with this.

Many thanks. :)

---

### Post by srs5694 on 2011-03-12
> **coffeecat said:**
> It was fun testing this. I shall no doubt be suggesting use of this in due course. Partition tables left bruised and bleeding by the Windows installer seem to be happening with monotonous regularity and this is going to be an excellent tool for dealing with this.

Yup. That, and problems caused by TestDisk, were the main reasons I wrote it. Fortunately, I'd already done most of the hard work -- gdisk already had a pretty complete set of MBR features, in support of its GPT-to-MBR functionality, so I was able to adapt those.

---

### Post by Telengard C64 on 2011-03-12
I hope I never need this tool to fix my partition table, but I'm very greatful just knowing it exists. Thanks very much for your efforts.

---

### Post by Pictor on 2011-03-17
I just discovered this new tool :o

I hope it will help me with the problems I'm having on my disk 

(instead of recovering GRUB I tried to restore partition table with TestDisk: now GParted say the disk is "unallocated" and a partition has become not mountable)

I'll take a look at your tutorials :KS

---

### Post by srs5694 on 2011-03-17
Pictor,

Chances are your disk is damaged in one of the ways that FixParts can handle. Check the utility's documentation, and if you've got any questions, please start a new thread on it. (Peoples' problems are often very unique, even when they seem similar to others' problems, so it's usually best to start a new thread about specific problems to keep each problem-solving thread focused. Note that I'm *not* criticizing your post in this thread; I'm just advising you on how to proceed from here.)

---

### Post by Pictor on 2011-03-21
Don't worry. I know you didn't want to offend me. :D
I wanted just to remark my case to know if yours could be the tool that suits my needs.
I had no time lately, so I'll try FixParts in the next days. I hope it will fix my problems just opening and saving the Partition Table ;)

Otherwise I'll start a new thread. :)

 Thank you!

---

