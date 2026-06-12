---
title: "300 out of 500 GB showing"
date: 2010-07-17
forum: General Help
---

### Post by RabbitWho on 2010-07-17
Hi hi, 
This doesn't seem to me to be particularly a ubuntu or windows problem, though i made the problem through windows.  so I'll post it here and on a Windows forum and if it turns out to be specific to windows then you guys can get mad at me and delete it. 
SO

My computer had too many failed OSs and partitions on it and blank space I couldn't access, it was a mess. and I got a free windows 7 upgrade CD from Dell, so I decided to nuke it and start fresh. 

I put the CD in, there was the simple upgrade button, didn't want that, went to the other option because i wanted to erase everything and start again. 
The next screen was a list of partitions.
 I deleted all partitions except the BIOS in the end. And popped windows 7 on, but it was only reading 300 GB.
Windows just says: Local disk: 297, no mention of other partitions under "Disk Management", when there was blank space or linux partitions in the past it read them.  

I was hoping all this would be solved when I tried to install Lucid, but it's only reading the 297GB as well. Because of this I assume Gparted will have the same problem

If I did something wrong there's no problem with starting everything over again, all i've installed is firefox on 7 and I'm running the Lucid live disk, but what should I do?

---

### Post by dino99 on 2010-07-17
better to use a real tool to check your devices and format your hdd

boot on partedmagic [http://partedmagic.com/](http://partedmagic.com/)

and look for hidden partitions and/or corrupted ones

at last, you can use specialised tool: [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by efflandt on 2010-07-17
What does **sudo fdisk -l** (small L) show for the drive (from a live/install CD if you have no other way to boot Linux on it)?

Not sure what you mean by "I deleted all partitions except the BIOS in the end."  There should not be any BIOS on the drive (that is a chip on the motherboard), but if you left some sort of Dell utility or recovery partition on the drive, that might block some use of the drive, especially if it is not right at the beginning or far end of the drive.

---

### Post by RabbitWho on 2010-07-17
[I]
Not sure what you mean by "I deleted all partitions except the BIOS in  the end."  There should not be any BIOS on the drive (that is a chip on  the motherboard), but if you left some sort of Dell utility or recovery  partition on the drive, that might block some use of the drive,  especially if it is not right at the beginning or far end of the drive.[/I]

Right so I deleted everything but hte Dell Utility, there was only one dell utility partition and I was careful to mind it. 

brb i'll try what you said, gotta go back into lucid

>  			 			 			 		   		 		 		better to use a  real tool to check your devices and format your hdd

boot on partedmagic [http://partedmagic.com/](http://partedmagic.com/)

and look for hidden partitions and/or corrupted ones

at last, you can use specialised tool: [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

mini howto: [http://ubuntuforums.org/showpost.php...4&postcount=14]("http://ubuntuforums.org/showpost.php?p=9216264&postcount=14")
 		                   		  		  		 		 			 				__________________ 


Thanks for your help! :) 


 I knew no part of this was going to be simple and straightforward! :S ;)

---

### Post by RabbitWho on 2010-07-17
here we go: 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55ca70e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6          18      102400    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              18       38914   312426496    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa37fdf86

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS



took a while to get back online, silly little problems i won't bore you with, now i can start looking for instructions on how on earth to get magicarp... magicparted working.

---

### Post by RabbitWho on 2010-07-17
[COLOR=#FFFFFF][FONT=georgia][B][FONT=arial][COLOR=Black]Argh guhfuhmamabalb! 

[http://partedmagic.com/documentation/130-creating-the-liveusb.html](http://partedmagic.com/documentation/130-creating-the-liveusb.html)

Trying to make it in windows, none of those "commands" work at all, it's not a command, it starts with a file name.. wtf..  I'm such a noob. I can't handle it, I'll try on linux tomorrow. 

tips? 
[/COLOR][COLOR=Black][/COLOR][/FONT][/B][/FONT][/COLOR]

---

### Post by RabbitWho on 2010-07-18
good morning bump!

---

### Post by RabbitWho on 2010-07-18
Got parted magic

It's still only showing the 300 or so GB (298.09)

What can I do? I think I have to send it back to Dell and ask them can they fix it.

---

### Post by RabbitWho on 2010-07-18
Never mind, it turns out I never had a 500 GB hard drive in the first place and I'm an idiot. 

Anyone who genuinely has this problem can check out the windows 7 help thread as well which was really useful: 
[http://www.sevenforums.com/general-discussion/98150-not-recognizing-all-hard-drive-300-500-gb-showing-2.html#post849538](http://www.sevenforums.com/general-discussion/98150-not-recognizing-all-hard-drive-300-500-gb-showing-2.html#post849538)

---

