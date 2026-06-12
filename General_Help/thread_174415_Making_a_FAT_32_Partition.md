---
title: "Making a FAT 32 Partition"
date: 2006-05-11
forum: General Help
---

### Post by sjpritch25 on 2006-05-11
I already installed Ubuntu Breezy Badger.  I would like to format some free space on my hard drive.  Is there a utilty in Ubuntu where i can format that free partition and make is FAT 32.  I have a lot of files i want to share between Windows and Linux.  Thanks in advance.  :)

---

### Post by KillrBuckeye on 2006-05-11
You could try using a GParted LiveCD:

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

There might be an easier way, but I'm not too experienced with partitioning/formatting.

---

### Post by ZylGadis on 2006-05-11
I have a better solution: make it ext3, and then google for a toolset that enables Windows to read/write to ext3. There is one, freely downloadable, but I can't remember its name.

---

### Post by sjpritch25 on 2006-05-11
Thanks, i will have to go back and change it.  I went ahead and made it FAT 32  and guess what.....  Windows didn't recognize it.   I will go ahead and change it to ext 3.

---

### Post by DOtSlaSHuCantCME on 2006-05-11
[QUOTE=sjpritch25]Thanks, i will have to go back and change it.  I went ahead and made it FAT 32  and guess what.....  Windows didn't recognize it.   I will go ahead and change it to ext 3.[/QUOTE]


Sure windows can read fat32  just  make your  fat32 lines look like the one bellow.
 dev/hda5       /media/hda5     vfat    iocharset=utf8,umask=0000       0       0   
  change,  /dev/hdxx )  and   /yourmountpoint/hdxx   to reflect your setup(where xx  is your harddrive
 number).

"the fourth row (iocharset=utf8,umask=0000" will give you read and write to your windows
partition.One side note,if your windows is on a NTFS file system (like xp),then you will have to find out what are the steps to make Ubuntu  read and write to NTFS.

A quick solution is to put xp on a 10 gig partition,and make like 2 or 3 fat32 partition to store your goodies(data,music,videos).

Heres another tip ,make a 5 gig partition  for XP and another 5 gigs and label this 5 gig  partition "program files" and manually install all your  programs from now on to your program partition. Now if you mess up wimdows and have to reinstall window all your programs are still there.(you might have to reinstall 2 or three,but its better than having to install 50 0r more programs,plus you know what programs you have no need to write them down (well maybe you should write them down anyways.):-D 


Hope this helped.............

---

### Post by Clay85 on 2006-05-11
[QUOTE=DOtSlaSHuCantCME]

Heres another tip ,make a 5 gig partition  for XP and another 5 gigs and label this 5 gig  partition "program files" and manually install all your  programs from now on to your program partition. Now if you mess up wimdows and have to reinstall window all your programs are still there.(you might have to reinstall 2 or three,but its better than having to install 50 0r more programs,plus you know what programs you have no need to write them down (well maybe you should write them down anyways.):-D 
[/QUOTE]

I** believe** if you have to re-install windows, it won't see any files that need to be written to the registry. So, you would have to reinstall every program that had written it self to the Windows registry. Or Windows won't see it.

I'm not quite sure if that is the case. I've tried to keep windows on one partition and all my files on another partition before, and I ran into mega problems. :(
Has anyone else had windows partition problems? Maybe it's just me.

---

### Post by DOtSlaSHuCantCME on 2006-05-11
[QUOTE=Clay85]I** believe** if you have to re-install windows, it won't see any files that need to be written to the registry. So, you would have to reinstall every program that had written it self to the Windows registry. Or Windows won't see it.

I'm not quite sure if that is the case. I've tried to keep windows on one partition and all my files on another partition before, and I ran into mega problems. :(
Has anyone else had windows partition problems? Maybe it's just me.[/QUOTE]

In my case i usually "Ghost" a new install instead of a cd reinstall ,so that might 
be the reason i dont have to reinstall all my proggies ,but usually i have to reinstall
like 5 or more because of the reason you pointed out.

---

### Post by KillrBuckeye on 2006-05-12
sjpritch25:  Did you use the GParted LiveCD to create that FAT32 partition?  Did you try to use Windows Disk Management to mount the partition?  Did it give you the option to format it?  I am curious because I used GParted on the Ubuntu LiveCD the first time I attempted my dual boot configuration, and it seriously screwed up the NTFS and FAT32 partitions I created.  The partitions were not accessible within Windows, and when I tried to delete them from Windows Disk Management it strangely caused some other logical partitions to be deleted unintentionally.  The reason I suggested the GParted LiveCD is that somebody told me that my problems were related to having an old version of GParted on the Ubuntu LiveCD, and that the GParted LiveCD running the latest version of the program would have no problems with NTFS or FAT32 partitions.  

If you used the GParted LiveCD and had problems mounting the FAT32 partition in Windows, then I would conclude that GParted should not be used to create any NTFS or FAT32 partitions.  When I created my NTFS and FAT32 partitions from Windows Disk Management, everything was fine.. stupid GParted...

---

### Post by DoktorSeven on 2006-05-12
Windows should be able to see Linux-formatted FAT32 partitions fine, as long as the System ID set to the partition is correct.

I have no idea how/if gparted does this (I didn't see an appropriate option) but if you aren't afraid of commandline tools, fdisk can do it:

**sudo fdisk /dev/hda** (or whichever physical drive you're doing; hda, hdb, sda, sdb, etc -- not the partition, like hda1, hdb2, sda1, etc).

At the prompt, enter **p** to print the partition information - notice the "Id" and "System" column to the right - for your FAT32 partition this should be Id "b" or "c" (System "W95 FAT32" or "W95 FAT32 (LBA)").  If not, you'll need to change it for Windows to recognize it.

Enter **t** at the fdisk Command: prompt to change the label; enter the partition number (the number after "hda"/"sda"/etc) at the "Partition number" prompt, then "c" at the "Hex code" prompt.

Then use **w** to save changes and exit.

**DISCLAIMER: CAREFUL USING THIS TOOL**, you can really mess things up if you don't use it correctly.  I can't be held responsible for mistakes in instructions... read the help menu (**m**) carefully...

---

### Post by sjpritch25 on 2006-05-15
Sorry for the delay,  Here is what i did.  I used Gparted and made a 44 gb partition Fat32.  But dummy me forgot that FAT32 doesn't recognize anything larger than 32gb.  Went into windows and had 17GB free????  Don't know why???  Using Disk Management i formated that free space (17GB) in Fat32.  How do i go about mounting it to Ubuntu.  Here is what i get when i run fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825       19457   125572072+   5  Extended
/dev/sdb5            3825        9295    43945776   83  Linux
/dev/sdb6            9296       13550    34178256   83  Linux
/dev/sdb7           13551       17120    28675993+  83  Linux
/dev/sdb8           17121       19337    17808021    b  W95 FAT32
/dev/sdb9           19338       19457      963868+  82  Linux swap / Solaris


sdb8 is the partition i made in Windows
sdb7 is the partition i made with Gparted

How do i mount these partitions and share them with windows???? 

Thanks for the help](*,)

---

### Post by vh1 on 2006-05-16
like someone before me, I suggest you format it as EXT3. to let windows access it you can download the program freely from [http://fs-driver.org/](http://fs-driver.org/)

---

### Post by Googler on 2006-05-16
[QUOTE=ZylGadis]I have a better solution: make it ext3, and then google for a toolset that enables Windows to read/write to ext3. There is one, freely downloadable, but I can't remember its name.[/QUOTE]

the utility called captain nemo you can find it here :
[http://www.runtime.org/captain.htm]("http://www.runtime.org/captain.htm")

---

### Post by sjpritch25 on 2006-05-16
Thanks Vh1,  That worked!!!!!=D>

---

