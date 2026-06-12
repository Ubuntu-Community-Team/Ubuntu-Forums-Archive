---
title: "Hdd is failling"
date: 2011-02-13
forum: General Help
---

### Post by MIKE SILVA on 2011-02-13
Hi!

I have an HDD Buffalo of 1 terabit who was falling on the floor by accident. 

However it worked well for a few days. Now I receive information that is an imminent disk failure. I was access it via USB and now I no longer access those files.

To try to recover the data I did the following:

I have a PC with Ubuntu 10.10 and main disk of 40G. I bought a 1.5 Terabyte HDD to store all the backup information and connect all the discs on the PC.

I open the Console, do &#8220;sudo fdisk &#8211;l&#8221;
And I get the following:

```
Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificador do disco: 0x00031820

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1        4661    37431296   83  Linux
/dev/sda2            4661        4866     1648641    5  Estendida
/dev/sda5            4661        4866     1648640   82  Linux swap / Solaris

Disco /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificador do disco: 0xcd45cd45

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sdb1               1      182400  1465127968+   7  HPFS ou NTFS

Disco /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificador do disco: 0x2cb86be3

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sdc1               1      121601   976760001    c  W95 FAT32 (LBA)
```



I don&#8217;t know so much how to work with the console, but I know there is a possibility to copy manually the folders and files from SDC to SDB. My problem is I don&#8217;t know the commands to &#8220;see&#8221; what files exist on SDC and then start copying to SDB.

I try to use Grsync, but Grsync can&#8217;t access to SDC.
I lose almost one day searching on the forums and at Google, but don&#8217;t found explanations how to do it. 

Can you give me information about what I need to do?

Please, help me!

Thanks in advance

Mike

---

### Post by CharlesA on 2011-02-13
What happens if you try to mount sdc1?

Assuming there isn't a cdrom mounted, run this:

```
sudo mount /dev/sdc1 -t vfat /cdrom/
```

---

### Post by SPr on 2011-02-13
nm

---

### Post by MIKE SILVA on 2011-02-13
> **CharlesA said:**
> What happens if you try to mount sdc1?

Assuming there isn't a cdrom mounted, run this:

```
sudo mount /dev/sdc1 -t vfat /cdrom/
```

Thanks for you interest.

Is not a CD-ROM, Is a HDD with 1 terabite, and I think is already mounted. 

How can I see what files/folders are inside: what commands?

Mike

---

### Post by CharlesA on 2011-02-13
It doesn't have to be a cdrom to be mounted to /cdrom/, you can mount anything to any empty folder.

If it's already mounted, run the *mount* command to find out where it is mounted.

---

### Post by MIKE SILVA on 2011-02-13
What I write there? - Sorry for my ignorance.

sudo mount /dev/sdc1 -t vfat

is ok?

---

### Post by MIKE SILVA on 2011-02-13
I have write:

sudo mount /dev/sdc1 -t vfat /cdrom/ 

and receive the information that is already mounted

---

### Post by CharlesA on 2011-02-13
Just run this:

```
mount
```

That'll show you where everything is mounted, look for sdc1

---

### Post by MIKE SILVA on 2011-02-13
I'll receive this info:

```
arcomedia@arcomedia:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/arcomedia/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=arcomedia)
/dev/sdb1 on /media/9414292A142910B2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1 on /media/UNTITLED type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
```

---

### Post by CharlesA on 2011-02-13
Ok. Try this:

```
cd /media/UNTITLED
```
Then run:
```
ls
```

You should get a list of files.

---

### Post by MIKE SILVA on 2011-02-13
The HDD led is blinkin for more then 10 minutes without showing information, this is normal?

---

### Post by MIKE SILVA on 2011-02-13
Ok, Now it shows something not so good:

ls: não consigo aceder a SHARE: Erro de Entrada/Saída de dados
ls: não consigo aceder a Recycled: Erro de Entrada/Saída de dados


This mean it can access to SHARE Folder - In/out data error (?)
and the same to recycled

Could it have more than one partition?

Because yesterday i saw it have data in use: 950 Gigabytes (more or less). I saw this after i connect the Buffalo Station by LAN. But no access to data.

---

### Post by CharlesA on 2011-02-13
No, that's not normal. If the drive fell, it's more then likely toast. Is the drive making any noise at all?

---

### Post by MIKE SILVA on 2011-02-13
At this moment no.
But at a few hours ago it was making a few "clicks" like a problem in the head, but the sound was diferent than that.

I have others HDD that "died" and the noise was diferent.

Could it be over heated? (HOT) - because is connect since this morning

---

### Post by CharlesA on 2011-02-13
Some clicking is normal, as that's just the heads moving around, but that only really happens when the drive is trying to spin up, once it's spinning you don't usually hear anything outside of the motor for the platters.

You could try putting it in the freezer for a few hours and try hooking it up again, but I have a feeling the drive is toasted.

---

