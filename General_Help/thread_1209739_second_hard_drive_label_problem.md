---
title: "second hard drive label problem"
date: 2009-07-10
forum: General Help
---

### Post by trkstff on 2009-07-10
Hi All
   Noob here.    Need alittle help please.   First couldn't access /dev/sdb1 drive but now i guess i can something i did in the name/name root permission.     Second while trying to setup /media/storage on /dev/sdb1 drive looks like i goofed with labeling of the drive and file.      I know how to get in the terminal just need to slow down and LEARN.   Thanks for any guidance

---

### Post by phillw on 2009-07-10
[SIZE=2][FONT=Arial]Hi

[/FONT][/SIZE]GParted 

[SIZE=2][FONT=Arial]will let you know what is connected..

I am puzzled over you saying 'label' - in Windows operating systems a volume has a label when you format it, if you specify one.

In linux hard disks are known as .....

[/FONT][/SIZE][SIZE=2]_Naming of partitions_.[/SIZE]

_Windows_: Windows uses lettering (c:\  ; e:\ , etc).

_Linux_: Linux uses /dev/hd[COLOR=red]x[/COLOR][COLOR=green]y[/COLOR] or /dev/sd[COLOR=red]x[/COLOR][COLOR=green]y[/COLOR] (most distros now use "/dev/sdxy", see below).

[COLOR=red]x[/COLOR] will be a letter starting with a, then b,c,....
[COLOR=green]y[/COLOR] will be a number starting with 1, then 2,3,....

Thus sda1 = First partition on the master HD.


[SIZE=2][FONT=Arial]The whole article is below - It is a full tutorial on linux file-sytems, so, take your time.
Rome wasn't built in a day - You have just started out on a wonderful voyage of discovery. On these forums you will find really brilliant people, always happy to help. Try that with commercially bought stuff !!!

Anyways, I digress ... the article ...

[http://ubuntuforums.org/showthread.php?t=282018&highlight=fstab](http://ubuntuforums.org/showthread.php?t=282018&highlight=fstab)

Not only will you find the answer, you will learn HOW to find the answer.

Regards,

Phill.
[/FONT][/SIZE][SIZE=2][FONT=Arial]

[/FONT][/SIZE]

---

### Post by michy99 on 2009-07-10
Linux partitions can also have labels. You can make and change them with gparted or with tune2fs.

---

### Post by trkstff on 2009-07-10
Hi Phil
   Here is info from my system monitor that doesn't look correct.    Shouldn't the second hard drive be /dev/sdb1
Thanks

---

### Post by trkstff on 2009-07-10
Hi Michy99
     Here is some more info that migh be helpful.
Thanks

---

### Post by michy99 on 2009-07-10
gvfs-fuse-daemon is a virtual file system, not an actual partition. If you have a second drive, it does not appear to be mounted. What output do you get from these commands?```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by trkstff on 2009-07-10
mike@mike-desktop:~$ sudo fdisk -l
[sudo] password for mike: 

Disk /dev/sda: 40.9 GB, 40971571200 bytes
255 heads, 63 sectors/track, 4981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e9b1c14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4817    38692521   83  Linux
/dev/sda2            4818        4981     1317330    5  Extended
/dev/sda5            4818        4981     1317298+  82  Linux swap / Solaris

Disk /dev/sdb: 40.9 GB, 40971571200 bytes
255 heads, 63 sectors/track, 4981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60bfe81c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4981    40009851   83  Linux
mike@mike-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  3.3G   32G  10% /
varrun                490M  216K  490M   1% /var/run
varlock               490M     0  490M   0% /var/lock
udev                  490M   52K  490M   1% /dev
devshm                490M   12K  490M   1% /dev/shm
lrm                   490M   40M  451M   8% /lib/modules/2.6.24-24-generic/volatile
gvfs-fuse-daemon       37G  3.3G   32G  10% /home/mike/.gvfs
mike@mike-desktop:~$

---

### Post by trkstff on 2009-07-10
mike@mike-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=90c97ee4-5b39-4aa7-bb09-2710fa1b4f77 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=79d11341-e4e7-4326-a5ea-4ac30d741a4e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by michy99 on 2009-07-10
How about```
cat /etc/fstab
```

---

### Post by trkstff on 2009-07-10
mike@mike-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)

---

### Post by michy99 on 2009-07-10
So you want to mount /dev/sdb1 at /media/storage, is that right? Do you want it automatically mounted when you boot?

---

### Post by trkstff on 2009-07-10
Yes i would like to mount /dev/sdb1 at /media/storage
Thanks

---

### Post by michy99 on 2009-07-10
First, make the mountpoint.```
sudo mkdir /media/storage
chown mike:users /media/storage
```Then edit fstab.```
gksudo gedit /etc/fstab
```Add this line:```
/dev/sdb1 /media/storage  ext3    relatime        0       2
```Save the file and reboot.

---

### Post by trkstff on 2009-07-10
mike@mike-desktop:~$ sudo mkdir /media/storage
[sudo] password for mike: 
mike@mike-desktop:~$ chown mike:users /media/storage
chown: changing ownership of `/media/storage': Operation not permitted

---

### Post by michy99 on 2009-07-10
Oops, that should be```
sudo chown mike:users /media/storage
```Sorry.

---

### Post by trkstff on 2009-07-10
Thanks Michy99

Do i now need to delete     gvfs-fuse-daemon /home/mike/gvfs    drive?

---

### Post by michy99 on 2009-07-10
To be honest, I don't really know much about the gvfs thing. I wouldn't mess with it until you find out from someone who knows more about it.

---

