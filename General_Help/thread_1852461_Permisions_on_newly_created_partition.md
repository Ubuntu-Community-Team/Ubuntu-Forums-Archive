---
title: "Permisions on newly created partition"
date: 2011-09-30
forum: General Help
---

### Post by gtdcubo on 2011-09-30
After a year of running a dual boot with Windows Vista and Ubuntu 10.10 I reached the point where I no longer needed windows, and moreover needed the space used up by the windows partition. Therefore, using GParted Partiton Editor, I unmounted the two NTFS Partitions and then deleted them. After this I created two new ext4 partitions using the free space liberated by the deletion of the NTFS partitons. The instructions I followed to do this can be found here. 

[http://askubuntu.com/questions/46863/how-do-i-remove-windows-7-from-my-dual-boot-system-with-ubuntu](http://askubuntu.com/questions/46863/how-do-i-remove-windows-7-from-my-dual-boot-system-with-ubuntu)

The creation of the new partitions passed without error. However, when I came to use these partitions I found that I was unable to do anything with them. In the GUI Places/Computer, the two partitions can be seen and I can navigate to them. They are called 133GB File System & 290 GB File System. WHen I attempt to create a folder in either of these locations I find that the menu item "right mouse/create folder" is greyed out. This is despite the fact that I have granted the Adminiostrator role to the logged in user. I would have expected this would be sufficient to allow me to create a folder wherever I liked. 

I have also tried to navigate to these partitions in a terminal session, but am unable to find them. That is to say, the two new partitions that I have created are called dev/sda1 & dev/sda2. However, navigating the directory dev there can be found 2 items sda1 and sda2, but these do not look like partitions. They appear more to be files that may contain metadata for the partitions in question (there is no way of knowing as the attempt to look inside these items produces the error "Could not display "/dev/sda1".There is no application installed for Block Device files") . I was assuming that I could navigate to these partitions and apply some kind of permissions to them that would allow my user to manage folders and file permissions therein.

I have a book called Ubuntu hacks but there are no sections on either partitons or folder & file security permissions. I think the author has assumed a prior-knowledge of Unix style security permisions which I do not have.

Basically I need to know the following
1. ¿How can I take control of my new partitions and start creating folders and files within them (either by GUI or Terminal)?
2. ¿How do I navigate to partitions in the Ubuntu file tree?

Thanks in advance for your attention

---

### Post by dcstar on 2011-09-30
> **gtdcubo said:**
> After a year of running a dual boot with Windows Vista and Ubuntu 10.10 I reached the point where I no longer needed windows, and moreover needed the space used up by the windows partition. Therefore, using GParted Partiton Editor, I unmounted the two NTFS Partitions and then deleted them. After this I created two new ext4 partitions using the free space liberated by the deletion of the NTFS partitons. The instructions I followed to do this can be found here. 

[http://askubuntu.com/questions/46863/how-do-i-remove-windows-7-from-my-dual-boot-system-with-ubuntu](http://askubuntu.com/questions/46863/how-do-i-remove-windows-7-from-my-dual-boot-system-with-ubuntu)
........

[LIST=1]
[*]Part of that HOWTO is basically rubbish. You should not **ever** manually mount anything in /mount. That is a **system** folder for the **system's** exclusive use when the **system** mounts devices.
[*]Use a tool like the **pysdm** package to automatically mount extra filesystems on your internal disks. Put the mount points in a non-system folder like /mnt or the root folder. Mount them with the same options as your existing filesystem.
[/LIST]

---

### Post by Morbius1 on 2011-09-30
I would not recommend pysdm for a whole number of reasons.

Why not post the output of each of the following commands so we can see what's up:

```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by gtdcubo on 2011-10-01
I see that the two respondents have offered conflicting suggestions. Thanks David and Mobius1 for your prompt replies. As I am not advanced enough in Linux to be sure what David is recommending, I am going with Mobius1 for now. 

```

paul@VLC-GF7050VT-M:~$ sudo blkid -c /dev/null
[sudo] password for paul: 
/dev/sda1: UUID="5111b62f-e489-49f3-8715-290edc73f4e6" TYPE="ext4" 
/dev/sda2: UUID="ea85a51d-7752-4042-88fc-06a15ec50ad5" TYPE="ext4" 
/dev/sda5: UUID="0709c49e-bf66-4c64-a7a8-35f9a02f58b4" TYPE="ext4" 
/dev/sda6: UUID="d3ece3c1-837c-4b4c-942a-65945829b043" TYPE="swap" 
/dev/sdf1: LABEL="PENDRIVE" UUID="8CA47AFCA47AE7DA" TYPE="ntfs" 
/dev/sdg1: LABEL="BACKUP02" UUID="2680A85480A82C6D" TYPE="ntfs" 
paul@VLC-GF7050VT-M:~$ 

```

```

paul@VLC-GF7050VT-M:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0709c49e-bf66-4c64-a7a8-35f9a02f58b4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d3ece3c1-837c-4b4c-942a-65945829b043 none            swap    sw              0       0
paul@VLC-GF7050VT-M:~$ 

```

```

paul@VLC-GF7050VT-M:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/paul/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paul)
/dev/sdf1 on /media/PENDRIVE type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2 on /media/ea85a51d-7752-4042-88fc-06a15ec50ad5 type ext4 (rw,nosuid,nodev,uhelper=udisks,commit=0,commit=0)
/dev/sdg1 on /media/BACKUP02 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
paul@VLC-GF7050VT-M:~$

```

---

### Post by Morbius1 on 2011-10-01
The best long term solution is to have these partitions autoumount when you boot.

Here is the produre I would follow if it were my partitions based on the information you posted:
> /dev/sda1: UUID="5111b62f-e489-49f3-8715-290edc73f4e6" TYPE="ext4" 
/dev/sda2: UUID="ea85a51d-7752-4042-88fc-06a15ec50ad5" TYPE="ext4"
/dev/sda2 on /media/ea85a51d-7752-4042-88fc-06a15ec50ad5 type ext4 (rw,nosuid,nodev,uhelper=udisks,commit=0,commit=0)[1] Unmount the partition you have mounted through Nautilus:
```
sudo umount /dev/sda2
```[2] Create permanent homes for your partitions to live in:
```
sudo mkdir /media/Data1
sudo mkdir /media/Data2
```[COLOR=Blue]*It doesn't have to be Data1 and Data2 just don't have spaces in them - it's easier that way.*[/COLOR]

[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Add the following lines to the end of fstab:
```
UUID=5111b62f-e489-49f3-8715-290edc73f4e6 /media/Data1 ext4 defaults,noatime 0 2
UUID=ea85a51d-7752-4042-88fc-06a15ec50ad5 /media/Data2 ext4 defaults,noatime 0 2
```[5] Save fstab and then run the following command that will test for errors and if there are none mount the new partition without requiring a reboot:
```
sudo mount -a
```[6] Verify that the partitions can be accessed though Nautilus then run the following commands to take possession of the mounted partitions so you can add files and folders:
```
sudo chown your-user-name /media/Data1
sudo chown your-user-name /media/Data2
```

---

### Post by gtdcubo on 2011-10-02
The solution indicated by Morbius1 has solved my problem. I have some post solution feedback questions

1. Can we assume from the need to create an explicit location for Data1 & Data2 in the media directory that the GUI tool GParted is not sufficient to carry out all the tasks associated with formatting and mounting a partition? 

2. I am a little confused as to why we both have to create the partition (which I did when I formatted the former NTFS partition to ext4) and explicitly nominate a logical storage area for the partition. I guess I am carrying some windows baggage where the act of formatting a partition is sufficient both name it and put it into use. 

I would appreciate a link to the area of the Ubuntu manual in which these issues are laid out. 

Thanks for you attention to this matter and thanks to both of you who replied.

---

### Post by CatKiller on 2011-10-02
You don't need to chown the mount point. You can set ownership options in fstab. Not at my computer, so I can't check whether it's user or users but it's one of them.

You aren't specifying a name for the partition, you're creating a mount point, the place where it fits into the filesystem tree. You can mount a partition in an existing place to fulfil a particular purpose - for example as /home or /boot or /var or whatever if you want to use a filesystem that's optimised for small files or redundancy, or just to organise things differently. Since the partitions you want to use aren't already included in the normal filesystem tree - you just want a flat data storage area - you need to create your own mount point.

---

### Post by Morbius1 on 2011-10-02
> 1. Can we assume from the need to create an explicit location for Data1  & Data2 in the media directory that the GUI tool GParted is not  sufficient to carry out all the tasks associated with formatting and  mounting a partition? You are correct. Gparted is used to manipulate the partition itself and fstab is used to mount the newly modified partition.
> 2. I am a little confused as to why we both have to create the partition  (which I did when I formatted the former NTFS partition to ext4) and  explicitly nominate a logical storage area for the partition. I guess I  am carrying some windows baggage where the act of formatting a partition  is sufficient both name it and put it into use. Actually, Windows and Linux are doing the exact same thing the only difference is Windows allows the user zero degrees of freedom as to where to mount the partition so it's able to do both operations in one utility. When you create a partition in Windows it will mount it automatically to only one location which is the equivalent of the Linux root ( i.e., "/" ) directory. "C", "D", "E", etc.. are all at the same level in the hierarchy. 

When you create a partition in Linux you can mount it anywhere.

---

### Post by Morbius1 on 2011-10-02
> **CatKiller said:**
> You don't need to chown the mount point. You can set ownership options in fstab. Not at my computer, so I can't check whether it's user or users but it's one of them.
He's not chown'ing the mount point he's chown'ing the mounted partition. Chown'ing the mount point before the mount will do nothing since the mount itself replaces whatever ownership and permissions existed on the original mount point. 

You can set ownership and permissions options for ntfs and fat32 partitions in fstab. You cannot do that for Linux filesystems. You can only do that after the partition has been mounted.

Also "user" and "users" will not do what you think it will do and in the context of an fstab entry where the goal is to auto mount a given partition at boot they are irrelevant, ignored, and not desirable.

---

### Post by CatKiller on 2011-10-02
> **Morbius1 said:**
> You can set ownership and permissions options for ntfs and fat32 partitions in fstab. You cannot do that for Linux filesystems. You can only do that after the partition has been mounted.

Gotcha. It's a while since I've done it, and that was in the context of a Windows filesystem. Good to know, thanks.

---

### Post by gtdcubo on 2011-10-21
Thanks to everyone who contributed to solving my problem. I have learnt a lot.

---

