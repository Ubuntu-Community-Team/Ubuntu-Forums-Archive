---
title: "Nautilus issue under 12.04 LTS"
date: 2012-04-27
forum: General Help
---

### Post by abhi_69 on 2012-04-27
[FONT=Arial Black][SIZE=3]Hello all,

i just installed Ubuntu 12.04 LTS, it's a fresh installation. but i'm having a problem with nautilus while accessing my NTFS partitions.
i have 3 NTFS partitions in my system. i automount them using NTFS-config.
but i can't access them from nautilus file manager. when i open them and going to access (double click to open folders etc.) nautilus crashes. i can access ubuntu's / and /home partitions though. problem is only with those NTFS partitions. Here is the error output i'm getting from terminal while accessing those partitions from nautilus:

[/SIZE][/FONT]```
nautilus
Initializing nautilus-image-converter extension
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension
Segmentation fault (core dumped)

```

[FONT=Arial Black][SIZE=3]is this a bug or so?

i already tried to remove gvfs-metadata from user's /local/share directory and reboot, but it's not working. actually this error killing me since installation.
Even this error happening under a Live CD session  (when i click to mount those partitions and going to access them) :(

here is the output of my /etc/fstab file, if this helps:

[/SIZE][/FONT]```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda6 :
UUID=5897dd60-fd0b-494f-bf06-f653c495b692    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda4 :
UUID=9E14064C1406283B    /media/MY_DRIVE    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda1 :
UUID=3B0164A859F2F294    /media/New_Volume    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda2 :
UUID=B09C301F9C2FDF1A    /media/PRIMARY    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda5 :
UUID=9286e73b-aa0c-419c-a8ff-bff9c3e0d420    none    swap    sw    0    0

```

[SIZE=3][FONT=Arial Black]*here's another info: i can access those file/folders while open them with 'Open with files' right-click menu. only double clicking or Open right-click menu giving me such error/problem.*

any idea guys?[/FONT][/SIZE][FONT=Arial Black][SIZE=3]
Thanks in advance.
Regards.
[/SIZE][/FONT]

---

### Post by deensokmo on 2012-04-27
I also have the same problem, what i need should do? I'm using Ubuntu 12.04 Beta 2 - final.. md5sum of ISO downloaded already check..

---

### Post by Harsh Kumar Narula on 2012-05-02
I had the same issue and had hard time to figure it out. I had one hidden file in the ntfs root drive, which was doing something wicked that nautilus could not handle and used to crash each time. I just deleted the file and yippey!!!, nautilus crash no more occurs.:guitar: You can try this and post whether it solves your problem or not. 

If it does not solve your problem then you should delete those files also which have strange character in their file names. Thanks

---

### Post by abhi_69 on 2012-05-04
> **Harsh Kumar Narula said:**
>  ... You can try this and post whether it solves your problem or not. 

If it does not solve your problem then you should delete those files also which have strange character in their file names. Thanks

thanks for your reply. but no, i don't have any such file with strange file name, just regular folders. currently i'm using Marlin and dolphin as file browser and both working very good with NTFS partitions; problem is with Nautilus only :(
still no clue why this is happening...

---

### Post by deensokmo on 2012-05-07
Today my problem SOLVED..:P. A few day I only use Marlin File Manager to handle NTFS partition/directori.

Many thanks to Harsh Kumar Narula, how to solved? I open Marlin, browse NTFS partition and delete **.hidden** file. This file I created  on previous ubuntu 11.10. Close Marlin and try to open Nautilus.. no more problem...

Now, I'm using 12.04.. enjoy..

---

