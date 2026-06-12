---
title: "Help with mutltiple SATA drives"
date: 2011-10-07
forum: General Help
---

### Post by studflucker on 2011-10-07
Hello Ubuntu forums, I'm glad to have been sent here by some fellow friends. Unfortunately, it is not on great terms. I've searched for this problem to no avail. So I'll lay it out for you.

I am(was) currently windows Vista 64 bit on an asus mother board. I have two SATA hard drives both are 500 GB. They are C: and F: 

Windows runs and boots from drive C: and F: is merely file storage

I used EaseUs to partition drive F: to 420GB and 60GB (roughly) so that I could install Ubuntu on the 60 GB partition of drive F: 

I inserted my cd-rom with Ubuntu on it, booted from CD and clicked install. When it asked whether or not I wanted to install alongside windows or do a fresh install I clicked the third option of "something else". This is where I selected the 60 GB partition, told it to go ahead and format it to EXT4 and to make this the boot partition. (all this on drive F: )

Now, I selected the 420GB partition of drive F: and checked to use as a swap drive. I made damn sure not to select the format option. The way I read it was that you could use that 420 Gig partition between ubuntu and windows. (Apparently I was wrong)

Now to the crooks of the matter. Ubuntu runs fine and I can even see drive C: through Ubuntu's file system. But when I boot through Windows Vista I can't see drive F: at all. It is no where to be found. My question is did I just lose all the data that was in the 420GB partition of that drive? And if not, how do I get windows to recognize it again, and continue to get to use Ubuntu alongside. I truly only will need the 60GB partition for Ubuntu, as I don't plan on using it for much more than learning some python and c code. (thus my whole reason for installing Ubuntu.) Also, if I need to reinstall Ubuntu to fix this, it is not a problem, I haven't done anything with Ubuntu so there is no harm in reinstalling. The only thing I am worried about is the data that was on the existing drive F:

Sorry for this being so long winded, I tried to be thorough, but if you have any questions, please ask. And thank you in advance.

---

### Post by YannBuntu on 2011-10-08
Hello, and welcome among us.
Please boot on your Ubuntu, then open a file browser, and check if you can access the data you are looking for. 
- If yes, copy it on c:/ or an external drive.
- if No: open a Terminal, then enter the following command:
```
sudo fdisk -l
```
enter your password (nothing will appear) then press Enter key.
And indicate us the output that will appear.

---

### Post by oldfred on 2011-10-08
STOP USING SYSTEM!!

Immediately:
```
sudo swapoff -a
```Swap is not shared. Swap is overflow for memory and is unformated space. Shared is a formated (usually NTFS) partition that both windows & Linux can read & write.

You do not want to boot from a Ubuntu liveCD as it will immediately mount the swap space & use it. Some liveCD do not use swap. I think you can set swap off as a parameter on liveCD boot but am not sure. Especially with liveCD use of swap will overwrite your data. If you have lots of RAM 4GB or more you may not have used much if any swap, so most of your data may be there, but file structure may also be damaged.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

What format was partition?

---

### Post by studflucker on 2011-10-08
> **YannBuntu said:**
> Hello, and welcome among us.
Please boot on your Ubuntu, then open a file browser, and check if you can access the data you are looking for. 
- If yes, copy it on c:/ or an external drive.
- if No: open a Terminal, then enter the following command:
```
sudo fdisk -l
```enter your password (nothing will appear) then press Enter key.
And indicate us the output that will appear.

john@john-System:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0b75ed4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       52850   424516601   82  Linux swap / Solaris
/dev/sda2           52851       60802    63866881    5  Extended
/dev/sda5           52851       60802    63866880   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd12e546a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204885504 bytes
1 heads, 63 sectors/track, 31008335 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2    31008256   976760032+   7  HPFS/NTFS

---

### Post by studflucker on 2011-10-08
> **oldfred said:**
> STOP USING SYSTEM!!

Immediately:
```
sudo swapoff -a
```Swap is not shared. Swap is overflow for memory and is unformated space. Shared is a formated (usually NTFS) partition that both windows & Linux can read & write.

You do not want to boot from a Ubuntu liveCD as it will immediately mount the swap space & use it. Some liveCD do not use swap. I think you can set swap off as a parameter on liveCD boot but am not sure. Especially with liveCD use of swap will overwrite your data. If you have lots of RAM 4GB or more you may not have used much if any swap, so most of your data may be there, but file structure may also be damaged.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

What format was partition?

After I run that command is it supposed to say anything??

Also, I have 8 gigs of ram. All night last night I booted into windows and downloaded a data recovery tool once I look in windows disk manager and it had no format for that partition with all my data on it. I was able to recover 99 percent of what was on the drive before. (btw that's the 1 TB drive above, I went and bought that to have a place to put the recovered data.) So I was able to recover what I need, thankfully. and nothing really important was lost. The whole recovery process took almost 16 hours. (451 GB recovered.)

So anyway, now that the crisis was averted how do I get the ~400 GB partition back available in windows and Ubuntu? Do I just format that partition in windows?

Thanks a bunch for the help.

---

### Post by oldfred on 2011-10-08
If you have all the data you can reformat it as NTFS.

You can try changing partition type without formating with disk utility. Change to HPFS/NTFS 0x07. If it was not really used it may actually be ok, Chances are not good, but worth a try. Data was there to be recoverable, but is the file format and directories to all the files. If it does convert, I expect it will need chkdsk from a Windows repairCD.

---

### Post by 3rdalbum on 2011-10-09
For future reference: For a desktop system that I imagine isn't going to be used as an intense workstation, 8 gigabytes of RAM is plenty and you won't need swap at all.

---

