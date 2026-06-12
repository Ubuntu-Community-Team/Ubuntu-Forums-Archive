---
title: "Strange /etc/fstab mounting behaviour"
date: 2010-04-19
forum: General Help
---

### Post by andrewwardrobe on 2010-04-19
Hi,

I'm using the lucid beta on one my machines, and have set up my /etc/fstab to mount my drives on start up. However this is never consistent between boots i.e sometimes my 750gb will get marked down as /dev/sdc1 an get mounted to /mnt/vol3 sometimes it will get marked as /dev/sdb1 and get mounted to /mnt/vol2, same for the other drives. I'm pretty sure its the drives hoping round device mappings because the output of a df seems to be correct with whats in /etc/fstab  

Output from df showing the mappings (note the used and available for each device)

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdf1            151845028   6024320 138107428   5% /
none                   2021528       312   2021216   1% /dev
none                   2028752       980   2027772   1% /dev/shm
none                   2028752       112   2028640   1% /var/run
none                   2028752         0   2028752   0% /var/lock
none                   2028752         0   2028752   0% /lib/init/rw
/dev/sdb1            732573040 658227396  74345644  90% /mnt/vol2
/dev/sda1            156288320  98433300  57855020  63% /mnt/vol1
/dev/sdc1            156280288 102613264  53667024  66% /mnt/vol3
/dev/sdd1            976760000 533075244 443684756  55% /mnt/vol4
/home/andrew/.Private
                     151845028   6024320 138107428   5% /home/andrew

```Output for a df after a reboot,notice some devices (/dev/s??/) have different sizes and the /mnt/vol? areas have swapped around

```
andrew@andrew-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdf1            151845028   6024624 138107124   5% /
none                   2021528       312   2021216   1% /dev
none                   2028752       192   2028560   1% /dev/shm
none                   2028752       112   2028640   1% /var/run
none                   2028752         0   2028752   0% /var/lock
none                   2028752         0   2028752   0% /lib/init/rw
/dev/sdb1            156288320  98433300  57855020  63% /mnt/vol2
/dev/sda1            156280288 102613264  53667024  66% /mnt/vol1
/dev/sdc1            732573040 658227396  74345644  90% /mnt/vol3
/dev/sdd1            976760000 533075244 443684756  55% /mnt/vol4
/home/andrew/.Private
                     151845028   6024624 138107124   5% /home/andrew
andrew@andrew-desktop:~$ 


```heres my /etc/fstab

```
andrew@andrew-desktop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde1 during installation
UUID=90351279-2d91-440c-8da9-aa9948d9841a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=17f7e218-773e-472d-b4ba-4939d3b13a94 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /mnt/vol2        ntfs  defaults  0 0
/dev/sda1       /mnt/vol1        ntfs  defaults  0 0
/dev/sdc1       /mnt/vol3        ntfs  defaults  0 0
/dev/sdd1       /mnt/vol4        ntfs  defaults  0 0

```So a few questions around that

[LIST=1]
[*]Anyone know why this could be happening? it doesn't do it when i boot into karmic (dual boot) so i'm not sure if its a mobo issue
[*]Should i be mapping my drives via a UUID? if how would find out the UUIDs?
[*]Could this be a bug in lucid? or have I just set something up wrong? i've done a apt-get update and upgrade but to no avail.
[/LIST]

Anyways if anyone could shed some light on this one I'd be very grateful

thanks

Andrew

---

### Post by Morbius1 on 2010-04-19
Open **Terminal**
Type **sudo blkid -c /dev/null**

It will output every partition with sdxy, UUID, and LABEL designations.

---

### Post by andrewwardrobe on 2010-04-19
Cheers mate I'll try mounting via UUID

---

### Post by andrewwardrobe on 2010-04-21
Seems to be stable now, using UUIDS.

---

