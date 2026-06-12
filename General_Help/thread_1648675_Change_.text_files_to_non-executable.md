---
title: "Change .text files to non-executable"
date: 2010-12-19
forum: General Help
---

### Post by Linyx on 2010-12-19
[SIZE="2"]I had some of Files in My NTFS partition, these files are TEXT-Files , but they are **executed** , So whenever i try to open these files, it shows me the Message which i have shown in **Screen-shot** [/SIZE]
[SIZE="2"]Everytime i had to select the **Display**,and its really annoying for me....[/SIZE]

However i had try to Change it to non-executed by the Command...

```
sudo chmod -x file-name
```

but doesn't succeed ,I think my NTFS-Drive is not **permitting** me to do this....
Moreover, when i run the above command, terminal doesn't give me an error....

Any suggestion..?

---

### Post by Wtower on 2010-12-19
NTFS partitions do not hold such information as linux permissions, they have their own arrchitecture of permissions and security implementations. For more information, take a look at:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

So, it is basically a matter of which permissions you assign when mounting the ntfs partition. I am afraid there is nothing you can else you can do to change individual files permissions using ntfs.

Regards

---

### Post by efflandt on 2010-12-19
When you double click, or right click on an executable "text" file in Nautilus (Places or File Manager) and click "Open", it is normal to ask you whether to:

[Run in Terminal] [Display] [Cancel] [Run]

Since DOS/Win file systems have no concept of execute permission, If you do not want that for FAT32 or NTFS, and you are mounting that partition with an entry in /etc/fstab, it sounds like you need to add **noexec** to the comma separated list of mount options (because exec is a default).  Not sure how to configure that if auto mounting a USB drive.

---

### Post by Linyx on 2010-12-19
[SIZE="2"]Thankx for both replies,

@efflandt 

 Where can i add **noexec**, I had attached my Fstab,[/SIZE]


```
[SIZE="2"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda8 :
UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca	/	ext3	errors=remount-ro	0	1
#Entry for /dev/sda6 :
UUID=32B4D35146D6CA5D	/media/Multimedia	ntfs	defaults,utf8,umask=007,uid=1000,gid=1000 0 1
#Entry for /dev/sda5 :
/dev/disk/by-uuid/232D470307EF2C88	/media/My_Data	ntfs	defaults,utf8,umask=007,uid=1000,gid=1000 0 1
#Entry for /dev/sda7 :
UUID=31d375a6-05be-4873-a867-d6acb273ec89	none	swap	sw	0	0
[/SIZE]
```

---

### Post by bodhi.zazen on 2010-12-19
> **Wtower said:**
> NTFS partitions do not hold such information as linux permissions, they have their own arrchitecture of permissions and security implementations. For more information, take a look at:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

So, it is basically a matter of which permissions you assign when mounting the ntfs partition. I am afraid there is nothing you can else you can do to change individual files permissions using ntfs.

Regards

Neither FAT or NTFS partitions support linux permissions and as indicated permissions of all files and directories are set when you mount the partition. You can use the options dmask, fmask, and umask

See: [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

