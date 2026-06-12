---
title: "Mounting two Hard disk after Installation"
date: 2011-07-05
forum: General Help
---

### Post by elliteforce on 2011-07-05
Hey Guys,
	Recently I had installed "Storage Device Manager", since because my hard drive partitions were not mounted correctly during installation.

	I own to hard disk "sda" 120 GB & "sdb" 1000 GB :), since during boot time i had mounted the "sda" having 3 partitions of windows on locations "/partion_name 1, 2, & 3" at root, and "sdb" was not mounted during instalation.

	After installation I had added "sdb" with my system and was working fine.

	But "sba" was mounted at "/partion_name 1, 2, & 3", But I wanted to change this type of partion what "sdb" i.e it should prompt me for the password when I use to mount it, So I tried to change the mount type for the "sba" But wasn't able to do this beacause of error "Disk is been used by other process".

	Now what i require is to mount "sda" partitions such as It may prompt for password when I try to mount and in "sdb1" having partions "sdb10" to be mounted automatically during boot time and the rest partions have to be prompted for password when I try to mount it.Is it possible..?

[B]*Please suggest me the whole procedure in manual manner(Command line) for the same:confused:
*Also using "Storage Device Manager"
*if I remove "Storage Device Manager" in future thus it effct my system partitions:confused:
*If I mount the partition in "/media/partion_name" thus it will solve my problem.[/B]:confused:


> [B]Details
UBUNTU 10.10
Harddisk:
sda : "sda1" mountpoint- "/win_xp"
      "sda5" mountpoint- "/win_7"
      "sda6" mountpoint- "/win"
sdb : "sdb10" mountpoint- "/media/Downloads"[/B]

**Please forgive me for my bad english and the mistake while writing the querry and please suggest what thing I had made wrong in it.**

**Thank You**

---

### Post by DawieS on 2011-07-05
You can look at the suggestion I made in this thread to adjust your password requirements (You will be able to set mounting, with or without password, to all your internal/external disk partitions)::smile:
[http://ubuntuforums.org/showthread.php?t=1490436](http://ubuntuforums.org/showthread.php?t=1490436)

---

### Post by elliteforce on 2011-07-05
Thanks Buddy.
But I'm not able to dismount any partition,it shows me a error what i had shown using image file

---

### Post by DawieS on 2011-07-05
> **elliteforce said:**
> Thanks Buddy.
But I'm not able to dismount any partition,it shows me a error what i had shown using image file
This is caused by other changes you have made, for example in **/etc/fstab**, including some partitions to "auto-mount" at boot-time. You will not be able to "normally" unmount these.

The method I suggested works for a default Ubuntu installation:
- The **/etc/fstab** file only reference the Ubuntu installation partition, and the Swap partition.
- All other drives and partitions, when powered on, will show unmounted in the nautilus file browser. If you click on one, it will be mounted, and a mount point will be created in **/media** by Ubuntu. If you click on the triangle next to the partition label, it will be unmounted, and the mount point in **/media** removed.

You may want to clean up your system, to look like a new installation, and revert the changes you have made. Type "**sudo gedit /etc/fstab**" in a terminal, to remove unwanted entries.

---

### Post by dcstar on 2011-07-05
> **elliteforce said:**
> 
........
	Now what i require is to mount "sda" partitions such as It may prompt for password when I try to mount and in "sdb1" having partions "sdb10" to be mounted automatically during boot time** and the rest partions have to be prompted for password when I try to mount it**.Is it possible..?
........

You can have partitions listed in the /etc/fstab file but with the "noauto" option - this means that they are not automatically mounted at boot but have to be specifically mounted with an individual mount command (do "man mount" for more details).

You need to do the following:

[LIST=1]
[*]Create separate mount points for your partitions outside of the /mount folder (this is a **system folder** only for dynamic mounts made by the system).
[*]Use the pysdm tool to then mount the partitions to the new mount points and add in the "noauto" option for those you do not want mounted automatically.
[*]Create scripts that you can launch to mount the manual partitions, for example: "gksudo mount /dev/sdb**x**" - this will prompt you for a password for each mount.
[/LIST]

---

### Post by elliteforce on 2011-07-07
Thanx guys for replying
But how to provide option of "noauto" to "/etc/fstab" for specific disk.
And I'm unable to demount any partition after been mounted

**My /etc/fstab detail**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda7 :
UUID=0f388088-76ef-4033-b82b-195eeaa29355	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda8 :
UUID=dc0fa29c-e1af-41f2-bed2-b67c0c659e1f	/home	ext4	defaults	0	2
/dev/sdb9	/media/Disk\040Images	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
#Entry for /dev/sdb10 :
UUID=CA741BE6741BD3D3	/media/Download	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
/dev/sdb8	/media/E-Books	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
/dev/sdb7	/media/Games	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
/dev/sdb5	/media/Movies	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
/dev/sdb1	/media/Music\040Videos	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
/dev/sdb6	/media/TV\040Series	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
/dev/sdb11	/media/Tempo	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
/dev/sdb1	/media/sdb1	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sdb11	/media/sdb11	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sdb5	/media/sdb5	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sdb6	/media/sdb6	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sdb7	/media/sdb7	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sdb8	/media/sdb8	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sdb9	/media/sdb9	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sda5	/media/win7	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
/dev/sda1	/media/win_C	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
/dev/sda6	/media/win_e	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
/dev/sda6	/win_e	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sda5	/windows7	ntfs-3g	defaults,locale=en_IN	0	0
/dev/sda1	/windowsXP	ntfs-3g	defaults,locale=en_IN	0	0
#Entry for /dev/sda9 :
UUID=eedc2ea9-a406-4132-9ea7-39b118cc947d	none	swap	sw	0	0
/dev/sdc	/media/sdc	vfat	defaults	0	0

```

Please suggest me,
How to make it auto mount those disk which i want and dismount them after using it..?
How to write the script for it..?

---

