---
title: "Seeking advice...is the following setup possible?"
date: 2006-06-24
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-24
hey all, I was wondering if I could actuallly do the following ** WITHOUT ** earasing windows... I want Windows and Linux to use the same files, same hard drive and all that... in more detail, I want windows to have its system files, and Linux to have its system files on the same partition...I'm not entirely sure if this is possible...but I want the 2 os's to share the same files on the same hard drive without having seperate partitions buggering it up. say I would download something on the windows os, and it would be on the same area so it would be viewable by the Linux os... is such a thing really possible?


----------------------------------------------------------------------------
second question

is it possible to install Linux on say an iPod or USB stick and have it be a read only type thing, and all the system files/configuration files would be saved to the hard drive? 




---------------

any answers are greatly appriciated. these are quite simple questions for those who know what they're doing, if I left out any info, please feel free to ask.


thanks.

---

### Post by bscbrit on 2006-06-24
In short - No.

You must have windows and linux on different partitions.  You _can_ have a data partition that can be read and written to by both OS but they must live apart from each other :-D

---

### Post by bscbrit on 2006-06-24
You do not have to erase windows to free up enough space to create a new partition.  Use a program like PartitionMagic to resize your existing Windows partition (defrag it first!) and then leave the resulting free space unallocated.  When you try to install ubuntu it will ask you if you want to use the unallocated space and it will take care of everything else for you.

---

### Post by aysiu on 2006-06-24
It's not possible. You need separate partitions.

---

### Post by AirRaven on 2006-06-24
The closest I can reccomend is installing Linux and Windows on their own partitions and formatting a third partition as FAT32 and storing your files there.

Setting all three partitions as FAT32 would make them readable by all OSes as well. You *could* try one of the Ext2/3 drivers for Windows, but in my experience they're rather unreliable.

---

### Post by Patrick-Ruff on 2006-06-24
well, NTFS was an option, what about that?

---

### Post by Ramses de Norre on 2006-06-24
Installing Linux on ntfs? I see two major problems with that:

# All programs that allow you to write on ntfs from Linux are still experimental and breakage of the file system is almost guaranteed..

# Your system will run sooo slow.. The ntfs drivers are a lot slower than any natively supported file system drivers.

So I'd say that's a no go..

---

### Post by Patrick-Ruff on 2006-06-24
ok well I suppose I wont attempt it then.

so, what kind of setup would I go for here? windows on NTFS, Linux on Ext3 or whatever, and then a blank space partition?

---

### Post by dmartinsca on 2006-06-24
I would install windows on NTFS, linux on a filesystem of your choice -- ext2/3, reiserfs, jfs, xfs, whatever -- and create a fat32 partition to share data.
You also have the option of installing windows on fat32 and linux on something else, that way linux can read and write to your entire windows partition and you don't need a third partition for data. The reason I give this as an option is that it's sometimes hard to guess ahead of time how much space you'll need for any given partition. By only having 2 partitions you leave less room for error!

---

### Post by handy on 2006-06-24
[QUOTE=dmartinsca]I would install windows on NTFS, linux on a filesystem of your choice -- ext2/3, reiserfs, jfs, xfs, whatever -- and create a fat32 partition to share data.
You also have the option of installing windows on fat32 and linux on something else, that way linux can read and write to your entire windows partition and you don't need a third partition for data. The reason I give this as an option is that it's sometimes hard to guess ahead of time how much space you'll need for any given partition. By only having 2 partitions you leave less room for error![/QUOTE]

Or more partitions if you have PartitionMagic installed on windoze.
NTFS is generaly accepted as being a more reliable file system than fat32.  Windoze needs all the help it can get, from my experience!

PartitionMagic allows you to resize fat, ntfs, ext2, ext3 & linux swap partitions, also convert partitions between these types - (back-up first), & much more.

I have used PartitionMagic for years in the windoze world, & have occasionaly had to resort to it in the linux world too. It is one of the only things I still keep a disk around with xp on it for!

In my experience, so far the linux alternatives to PartitionMagic are unfortunately not as good.  
When they are as good I will happily reformat that windoze drive & be rid of it forever!! :KS

---

### Post by Patrick-Ruff on 2006-06-25
believe me, I would straight up get rid of windows completely...but, heres the delema..dialup modem. its strange, I was able to dialup, it connected, but the internet never really worked. I didn't really understand it...I mean the modem was detected, it DID dial, I heard all the noises and everything, but it never actually connected, almost as if it was denyed that very second...

---

### Post by handy on 2006-06-26
[QUOTE=Patrick-Ruff]believe me, I would straight up get rid of windows completely...but, heres the delema..dialup modem. its strange, I was able to dialup, it connected, but the internet never really worked. I didn't really understand it...I mean the modem was detected, it DID dial, I heard all the noises and everything, but it never actually connected, almost as if it was denyed that very second...[/QUOTE]

I'd take that one to the **Networking** forums!

---

### Post by 23meg on 2006-06-26
You can use a EXT2/3 driver for Windows that will let you read and write files on Linux EXT2 and EXT3 partitions so that you won't need a separate data partition for sharing files between the two OSes. This one is freely available and works very well:  [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by handy on 2006-06-27
[QUOTE=23meg]You can use a EXT2/3 driver for Windows that will let you read and write files on Linux EXT2 and EXT3 partitions so that you won't need a separate data partition for sharing files between the two OSes. This one is freely available and works very well:  [http://www.fs-driver.org/](http://www.fs-driver.org/)[/QUOTE]

Thanks, that's good news for sure!!

---

