---
title: "Ubuntu won't  move my files"
date: 2011-08-30
forum: General Help
---

### Post by inabitofapickle on 2011-08-30
HI. I have to move a movie file (4.3 GB) from my laptop to my desktop, and it always says file to large to move, it only loads 4 GB and thats it. what should i do?

---

### Post by rickyjones on 2011-08-30
> **inabitofapickle said:**
> HI. I have to move a movie file (4.3 GB) from my laptop to my desktop, and it always says file to large to move, it only loads 4 GB and thats it. what should i do?

What OS does each system use? 

Thanks,
Richard

---

### Post by claracc on 2011-08-30
I think that it is a problem related to the type of format of partitions in HD.

If the destiny HD is fat32, it won't let copy more than 4 GB files, you have to format in ntfs, assuming your desktop is windows.

---

### Post by seawolf167 on 2011-08-30
If you run the following command and post the results in CODE tags we can see if the issue is related to the partition format type

```
sudo blkid
```

---

### Post by inabitofapickle on 2011-08-30
Windows 7 & ubuntu 10.04

---

### Post by inabitofapickle on 2011-08-30
Umm, how would i move this file?

---

### Post by seawolf167 on 2011-08-30
From which computer to which computer? How are you moving the file? Are you using Samba over your LAN or via a flash drive? Please post more details of what you are attempting.

---

### Post by BlinkinCat on 2011-08-30
Note seawolf167's comments

---

### Post by inabitofapickle on 2011-08-30
seawolf 

> /dev/sda1: UUID="eb3acceb-9904-4cca-b219-c602090ebc65" TYPE="ext4"
/dev/sda5: UUID="c2359b08-48e7-49f3-8683-06679ef504d4" TYPE"swap"
/dev/sdb: LABEL="PENDRIVE" UUID="3AC@ 39FC" TYPE="vfat"

---

### Post by inabitofapickle on 2011-08-30
I am moving from linux to windows

---

### Post by LMP900 on 2011-08-30
The flash drive is likely formatted in FAT32, which means you cannot transfer files larger than 4GB. You can either:

[LIST]
[*]Format your flash drive as NTFS
[*]Break up the movie files using a utility like 7zip
[/LIST]

---

### Post by mcduck on 2011-08-30
> **inabitofapickle said:**
> I am moving from linux to windows

I assume you are trying to move the file to your pen drive, which according to that output is formatted in FAT.

FAT has a maximum file size of 4GB, so you'll have to either format the drive to some more modern filesystem, or split your file in some way or other. A common method is to compress the file into a split .rar archive, giving you multiple small files instead of one big one.

---

### Post by seawolf167 on 2011-08-30
> **mcduck said:**
> I assume you are trying to move the file to your pen drive, which according to that output is formatted in FAT.

FAT has a maximum file size of 4GB, so you'll have to either format the drive to some more modern filesystem, or split your file in some way or other. A common method is to compress the file into a split .rar archive, giving you multiple small files instead of one big one.

+1, note from the output of the command you posted for me that your "PENDRIVE" is formatted as "vfat". As stated, the max file size is 4GB. Since your destination is Windows, the *split* command won't work, you'll want to either make a multipart archive, reformat your pendrive to a different format, or transfer the file via your network.

---

### Post by inabitofapickle on 2011-08-30
sea wolf. i'm dragging and droping to my falsh drive

---

### Post by seawolf167 on 2011-08-30
> **inabitofapickle said:**
> sea wolf. i'm dragging and droping to my falsh drive

Yes - the problem is with your flash drive. It's format (vfat) is incapable of handling files whose sizes are greater than 4GB. You'll need to use another method mentioned above to transfer these files to your other computer.

---

### Post by inabitofapickle on 2011-08-30
what should I do seawolf?

---

### Post by rickyjones on 2011-08-30
> **inabitofapickle said:**
> what should I do seawolf?

The best solution may be to reformat the flash drive to use the NTFS filesystem. Windows 7 will recognize it, so will Ubuntu, and it will accept files larger than 4GB.

Thanks,
Richard

---

### Post by seawolf167 on 2011-08-30
> **inabitofapickle said:**
> what should I do seawolf?

You can either use a program to split the file into smaller parts like 7zip, rar, etc. 7zip should have a right-click context menu if I'm not mistaken, and can be installed through the terminal by typing the command

```
sudo apt-get install p7zip-full
```

You can also transfer the files over your network. There are tons of resources with pictures of each step that can be found through Google. [URL="http://www.liberiangeek.net/2011/04/share-files-folders-ubuntu-11-04-natty-narwhal/"]Here is one example.
[/URL]
You can also reformat your pendrive to something other than vfat that Windows can read - so NTFS. You can do this by running GParted (hit [ALT][F2] then type in GParted), once GParted opens, you can select your device from the upper-right hand corner and select to reformat the drive. Note that this will completely erase everything on the device when formatting.

---

### Post by inabitofapickle on 2011-08-30
Thanks a million!

---

### Post by seawolf167 on 2011-08-30
No problem! Glad you got this solved

---

### Post by BlinkinCat on 2011-08-30
Glad your still around inabitofapickle - :P

---

