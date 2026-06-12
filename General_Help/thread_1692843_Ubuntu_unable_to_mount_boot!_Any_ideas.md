---
title: "Ubuntu unable to mount/ boot! Any ideas?"
date: 2011-02-22
forum: General Help
---

### Post by listerdl on 2011-02-22
Hi I have a dual boot set up which was working just fine.

I installed a Grub2 Customizer as per a ubuntu tutorial: [http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183) and things have gone weird since this installation. (I am sure it is a great program but for me it seems to have caused the linux partition to refuse to boot).

When I boot into Ubuntu I get this message:

An error occurred while mounting : D Storage*
Press S to Skip mounting or M for Manual Recovery.

* D Storage is the name of a partition which both windows and ubuntu share.

OK when I skip nothing happens just a black dead screen. When I press M a terminal seems to open - any ideas what to do here?

I luckily made a clonezilla image just a few days ago and I thought to re-install the image but clonezilla refused - sorry I didnt record that message.

Any ideas what I have done here!!!

Thanks!!!!

PS It is worth mentioning that my entire grub was hosed but I used an amazing disk called supergrub which fixed the Grub 2, the above mentioned customizer version, but again, when I try to boot into ubuntu I get the above message.

Thanks

I though also to include an image of my set up, (had to use the windows version of disk management)

[IMG]http://www.georgedalziel.com/setup.png[/IMG]

---

### Post by listerdl on 2011-02-22
And also I ran these commands using the terminal when I went through the Manual Stage - hope this help! [COLOR="Red"]My commands are in red.[/COLOR]

[COLOR="Red"]mount[/COLOR]

/dev/sda3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nousid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
[COLOR="Red"]
sudo fdisk -l[/COLOR]

Disk /dev/sda: 128.0 GB 1280356726160 bytes
255 heads, 63 sectors/trac, 15566 cylinders
Unit = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01eb4677

Device Boot		Start		End		Blocks		ID		System
/dev/sda1		5399		15251	79136917+	7		HPFS/NTFS
/dev/sda2 **	14			2562	20474842+	7		HPFS/NTFS
/dev/sda3		2563		5111    20474842+	83		Linux
/dev/sda4		5112		5298	2305327+	82		Linux swap/ Solaris

Partition table entries are not in disk order

[COLOR="Red"]ls /dev/disk/by-uuid - alh[/COLOR]

ls: cannot access -: No such file or directory
ls: cannot access alh: No such file or directory
/dev/disk/by-uuid:
2776826342DA034E 38A4DA815BF26253 3d2asfaf311-d00d99sdda

---

### Post by Zimmer on 2011-02-22
Not sure what you might have done for the original error (other than maybe the space in D Storeage is not helpful to the workings of the customizer...  try renaming it with no spaces... :) )

Also, if you used Supergrub disk to recover you may have loaded legacy GRUB, not GRUB2 (see here  [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) )

I would suggest you try to uninstall the customizer and reinstall GRUB2 . 

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

[https://answers.launchpad.net/grub-customizer/+faq/1355](https://answers.launchpad.net/grub-customizer/+faq/1355)

---

### Post by matt_symes on 2011-02-22
Hi

This command 

```
ls /dev/disk/by-uuid - alh
```

should be this

```
ls /dev/disk/by-uuid -alh
```

Kind regards

---

### Post by matt_symes on 2011-02-22
Hi

Try running chkdsk on the partition from windows.

In Ubuntu, from a liveCD, open a terminal and type

```

sudo mkdir /mnt/storage
sudo mount -t ntfs /dev/sda1 /mnt/storage/
cat /mnt/storage/etc/fstab
```

I'm pretty sure sda1 is your D:\ storage partition but they are out of order. You can check by typing (from the liveCD)

```
sudo blkid
```

and checking the drive label matches sda1.

Post the results back here. 

You have unallocated space at the start and end of the drive. Might i suggest using an extended partition at some point and adding logical partitions inside it. If you change you partition table _always_ clone your drive first.

Kind regards

---

### Post by listerdl on 2011-02-22
thanks v v much really appreciate your help. Ill post back when I have a chance to access the machine.

---

### Post by listerdl on 2011-02-22
OK, didnt seem to work unfortuantely....(all done from Live Disk)

[COLOR="Red"]This all worked fine - didnt throw any error....[/COLOR]
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/storage
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /mnt/storage
ubuntu@ubuntu:~$ cat /mnt/storage/etc/fstab
```

[COLOR="Red"]But this did...[/COLOR]
```
cat: /mnt/storage/etc/fstab: No such file or directory
```

As suggested, I did double check that my Storage Partition was sda1 which it is:
```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
[COLOR="Blue"]/dev/sda1: LABEL="Storage" [/COLOR]UUID="2776826342DA034E" TYPE="ntfs" 
/dev/sda2: LABEL="Windows7" UUID="38A4DA815BF26253" TYPE="ntfs" 
/dev/sda3: UUID="78131cc1-652b-4d74-ad4f-9133d446ac4b" TYPE="ext4" 
/dev/sda4: UUID="3d2c2f1d-d0d0-4242-8da6-fe671fafb033" TYPE="swap" 
```

The Ubuntu partition is on sda3 so I thought to change the last line to sda3 rather than sda1 (b/c that is where the ubuntu partition is, Storage is simply a shared NTFS partition with, or rather from Windows)

```
ubuntu@ubuntu:~$ cat /mnt/sda3/etc/fstab
cat: /mnt/sda3/etc/fstab: No such file or directory
```

Unfortunately same error....

For interest, I ran this line which achieved the following results:
```
ubuntu@ubuntu:~$ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root 120 2011-02-23 11:58 .
drwxr-xr-x 6 root root 120 2011-02-23 11:58 ..
lrwxrwxrwx 1 root root  10 2011-02-23 11:59 2776826342DA034E -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-02-23 11:59 38A4DA815BF26253 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-02-23 11:59 3d2c2f1d-d0d0-4242-8da6-fe671fafb033 -> ../../sda4
lrwxrwxrwx 1 root root  10 2011-02-23 11:59 78131cc1-652b-4d74-ad4f-9133d446ac4b -> ../../sda3
```

Any other ideas to get my partitions to mount as they used to?

**[COLOR="Indigo"]Thanks v much[/COLOR]**

---

### Post by matt_symes on 2011-02-23
Hi

Sorry about that. I was trying to do 5 things at once yesterday including fixing a crash on my friends XP machine when booting up. Somehow i managed to misread your post and what i wrote yesterday was totally Collocks. Attention too much divided i think.

Try this..

```
sudo mkdir /mnt/sda3
sudo mount -t ext4 /dev/sda3 /mnt/sda3
cat /mnt/sda3/etc/fstab
```

and post back the results of fstab in the last line.

Kind regards

---

### Post by listerdl on 2011-02-23
Hey thanks VERY much for your help with this!

OK! 

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/sda3
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda3 /mnt/sda3
ubuntu@ubuntu:~$ cat /mnt/sda3/etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=78131cc1-652b-4d74-ad4f-9133d446ac4b / ext4 errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=c28c6060-2a46-4e4b-adf7-0b4703dce9cc none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda4 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0
ubuntu@ubuntu:~$ 

```

[COLOR="Red"]****[/COLOR] sda1 is the "storage" shared partition which is the problem one which fails to mount. Should I have replaced the above /mnt/sda3 for sda1 ?

Thanks

---

### Post by listerdl on 2011-02-23
How about doing this:

```
fsck /dev/sda1
```

Since sda1 is my partition that is not mounting?

Before trying id rather have someones opinion! thanks

---

### Post by listerdl on 2011-02-24
bump - 

anyone pls?

Does anyone know how to remount a shared partition from the above info?
[B]
Id really appreciate any advice - thanks[/B]

Could it be an issue with the /etc/fstab code?

---------------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda3 :
UUID=78131cc1-652b-4d74-ad4f-9133d446ac4b	/	ext4	errors=remount-ro	0	1
[COLOR="Red"]#Entry for /dev/sda1 :
UUID=2776826342DA034E	/media/Storage	ntfs	defaults,nls=utf8,umask=0222	0	0[/COLOR]
#Entry for /dev/sda2 :
UUID=38A4DA815BF26253	/media/Windows7	ntfs	defaults,nls=utf8,umask=0222	0	0
UUID=c28c6060-2a46-4e4b-adf7-0b4703dce9cc	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
#Entry for /dev/sda4 :
UUID=3d2c2f1d-d0d0-4242-8da6-fe671fafb033	/media/Storage	ntfs-3g	defaults,locale=en_US.UTF-

---

