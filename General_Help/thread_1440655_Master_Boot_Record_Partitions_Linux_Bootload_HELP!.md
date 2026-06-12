---
title: "Master Boot Record/ Partitions/ Linux/ Bootload/ HELP!!!"
date: 2010-03-27
forum: General Help
---

### Post by gavlar on 2010-03-27
OK.
 
So I've a dual-boot system for some time with Windows XP and Ubuntu Linux.
 
I rarely use Linux, only for the odd utility that isnt in Windows or accessing files/doing things that Windows restricts. 
 
My 500gb HDD was split into 4 partitions: C: 100GB XP (NTFS), D: 50GB Ubuntu (EXT3), E: 50GB no idea why I had that (Unformatted) and a F: 300GB File Storage (FAT32).
 
Due to the fact that I sometimes need to work cross-os i had the F: drive in FAT32 so I could access it from Linux. Then Ubuntu became NTFS compatible and I didnt really need it in FAT32 anymore.
 
Due to FAT32's file size limitations (4GB or thereabouts) I needed to store large files on my C: drive. Therefore, enevitably my 100GB drive became full. I thought it would be a good idea to reformat my F: drive into NTFS so I could store said large files on the file storage partition. 
 
So, I looked at my F: drive and realised that if I deleted old HDD backups and the like I could reduce the size of the files I actually wanted on that drive to about 80GB. So I planned to delete the E: drive, shrink the D: drive 30GB make a new partition of 80GB, move the files I needed onto the 80GB then reformat the 300GB into NTFS and move them back.
 
I got as far as: Booting into Ubuntu to use the G-Parted tool, Deleting E:, shriking D:, making 80GB partition. The I was going to boot into windows to move the files (Dont know why I didnt do it in Ubuntu). HOWEVER, when restarting I got the usual "GRUB [the ubuntu bootloader I use] Loading..." message then "Error 22" and it just hung there. 
 
The I grabbed my Ubuntu disk and did a live boot off of that. Did a google for GRUB error 22 and found somewhere someone said to reset the Master Boot Record. So I grabbed my XP Disc and booted into the recovery consol and ran the FIXMBR command. The caution said that as my Drive has multiple partitions they would become unusable after the MBR was reset. So I didnt confirm it. 
 
Now Im booted on a live Ubunut CD and what Im actually asking it:
1) Will resetting the MBR make my other partitions unusable? I know it will screw with my bootloader causing me not to be able to boot into Ubuntu but have I misunderstood the warning; will it render my partitions unusable?
2) Will resetting the MBR actually help? I mean, will I be able to boot into windows then reinstall a bootloader and all will be fine?
3) If no, how can I fix this problem??? 
 
 
Sorry for the long post, but Im really stuck here. Please help, provide any infomation you can as Ive really no clue what to do now.
 
Thanks in advance for all of your help, 
Gavin [IMG]http://static.techguy.org/smilies/smile.gif[/IMG]

---

### Post by MichaelSammels on 2010-03-27
Wow, confusing. I think that by using FIXMBR you will knacker GRUB even more. I think it's because maybe (and I could be wrong here), the E:\ drive was being used as a /dev/sda1 (/boot) and /dev/sda2 (/swap) for Linux. Since GRUB boots off /dev/sda1, where the kernel is located, it couldn't find anything.

I may be wrong though.

---

### Post by gavlar on 2010-03-27
Thank you for your fast response this was orriginally a post on another forum but though Id double post it to see if I could get an answer. So sorry that the drives were in windows not linux :)

Im sorry but I'm abit of a linux noob. I think I got the gist of what you said.

Looking at the GParter tool I can tell you that:
C: is dev/sda1
D: is dev/sda2 and dev/sda6 for the swap (neither are reconised in windows so I thought it was one partition, as im a linux noob)
E: is now nonexistant as I deleted it and used the space to expand the F:
F: is dev/sda5

I dont know if that helps but there you go :/

I really am hoping for a solution.
Like I said eariler, I dont use Linux much so if I could scrap the bootloader and just boot into windows I think I could cope. Then I could install ubuntu via wubi.

Thanks for your help
Gavin

---

### Post by gavlar on 2010-03-27
Nevermind,
got bored and ran FIXMBR anyway and my partitions are fine.

(Although GRUB is completely gone as I suspected)

I think ill live boot into ubuntu and reformat the ext3 partitions into ntfs then use wubi to install ubuntu this time around.

---

### Post by MichaelSammels on 2010-03-28
Basically you boot into Ubuntu via LiveCD and remove ALL partitions without formatting and then format during Windows install.

---

### Post by oldfred on 2010-03-28
This is how to repair MBR for whatever operating system you want:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Wubi is ok for those who are windows centric. It is running on the NTFS partition so any windows issues can prevent you from booting Ubuntu. I suggest you keep your dual boot, with you data in different partitions the Ubuntu install does not have to be very large. Then you can boot either windows or Ubuntu.

---

