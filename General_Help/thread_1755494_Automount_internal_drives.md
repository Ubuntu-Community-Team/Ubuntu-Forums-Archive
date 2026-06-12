---
title: "Automount internal drives?"
date: 2011-05-11
forum: General Help
---

### Post by ischemic on 2011-05-11
I'm in the process of moving my current ubuntu/boxee media server from an Acer Revo with multiple external drives to an HP Microserver with the drives now internal. I've also taken this opportunity to move from 10.04 to 11.04.

I have transmission set to auto start but I always get an error about files not found - I need to then quit transmission, go to the file explorer and then open my non system disks. If I then restart transmission then it's all okay. I didn't have this issue with the drives being external/usb on the old system. They're all formatted ext4.

Is there anyway I can have them automount?

Also, as an aside - is vdpau installed by default in 11.04?

---

### Post by neu5eeCh on 2011-05-11
Have you tried the usual? - editing fstab?

You sound like you already have some experience with this, so if my question sounds obvious, my bad.

---

### Post by ischemic on 2011-05-11
I have done in the past. I'm a simple minded OSX user now though and was hoping to avoid too much config file wrangling. Guess I'll give that a go.

---

### Post by ambdeep on 2011-05-11
install storage device manager from ubuntu software center. I has a simple gui which will help you with your problem.

---

### Post by seawolf167 on 2011-05-11
I would suggest using

```
sudo apt-get install pysdm
```

to create your /etc/fstab entries for you if you don't want to do it manually

---

### Post by ischemic on 2011-05-11
Okay, I tried using pysdm and now everthing is a bit of a mess. I keep getting a message when I boot up that one of the drives can't be mounted (need to press s) - seems to keep changing. The drive names mounted on the desktop don't match the ones in my fstab at all. I've resorted to just editing fstab but I can't get things to work.

My current fstab:

```


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=e1e4ff3f-c1e0-4070-98d8-cf432ec476b2  /                ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=be8a54e0-36e6-4f27-bf1a-4d987e2ad6ef  none             swap  sw                   0  0  
/dev/sdc1                                  /media/airmax    ext4  defaults             0  0  
/dev/sdd1                                  /media/Serenity  ext3  defaults             0  0  
/dev/sde1                                  /media/ecto1     ext3  defaults             0  0  
/dev/sdb1                                  /media/delorean  ext4  defaults             0  0  

```

fdisk -l has this:

```


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004c1a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29749   238956544   83  Linux
/dev/sda2           29749       30402     5239809    5  Extended
/dev/sda5           29749       30402     5239808   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00041532

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02e0f418

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           2    31008256   976760032+   7  HPFS/NTFS

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002dcc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976758784    7  HPFS/NTFS

```

I don't get why two of the drives are reporting as HPFS/NTFS - I formatted them in ubuntu as ext3/4 (they were external drives so came preformatted though.

I've included a screen shot of my disk utility which shows the drive that's not mounting (I don't get the difference between partition type and type...)

Any ideas?

Thanks

---

### Post by Morbius1 on 2011-05-11
Stop using any GUI at least until we see some real data. Please post the output of the following commands:
```
sudo blkid -c /dev/null
```
```
mount
```

---

### Post by ischemic on 2011-05-11
```


/dev/sda1: UUID="e1e4ff3f-c1e0-4070-98d8-cf432ec476b2" TYPE="ext4" 
/dev/sda5: UUID="be8a54e0-36e6-4f27-bf1a-4d987e2ad6ef" TYPE="swap" 
/dev/sdb1: LABEL="delorean" UUID="150d3133-81cd-44d1-b269-4c7c86fcf4ad" TYPE="ext4" 
/dev/sde1: LABEL="ecto1" UUID="d7901fed-2474-461d-806e-e93cc07b86ac" TYPE="ext4" 
/dev/sdd1: LABEL="New Volume" UUID="8b686845-d6c0-46b0-a055-b589253983cd" TYPE="ext3" 
/dev/sdc1: UUID="998d78c6-783c-4c38-98b9-7d8e0f58f827" TYPE="ext3" 

```

```
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
/dev/sdc1 on /media/airmax type ext4 (rw,commit=0)
/dev/sdd1 on /media/Serenity type ext3 (rw,commit=0)
/dev/sdb1 on /media/delorean type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bradlay/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bradlay)

```

---

### Post by Morbius1 on 2011-05-11
For one thing your fstab entry for /dev/sde1 is incorrect:
> /dev/sde1 /media/ecto1     **[COLOR=Blue]ext3[/COLOR]**  defaults             0  0  Because the partition is ext4:
> /dev/sde1: LABEL="ecto1" UUID="d7901fed-2474-461d-806e-e93cc07b86ac" TYPE="**[COLOR=Blue]ext4[/COLOR]**" 
Edit fstab directly as root:
```
gksu gedit /etc/fstab
```Make the change in the filetype from ext3 to ext4.
Save fstab
Exit gedit
And back in the terminal run the following to test for errors ( and post them is there are any ) and mount the new partition without a reboot:
```
sudo mount -a
```

[COLOR=Blue]EDIT:[/COLOR] Your sdc1 is incorrect as well. We'll fix that next.

---

### Post by ischemic on 2011-05-11
Awesome thanks. That appears to of mounted okay. I assume sdc1 just needed changing to ext3 as well?

Right, now I just need to solve screen tearing on fullscreen videos (a story for another thread I think) and I'm sorted.

---

### Post by Morbius1 on 2011-05-11
> I assume sdc1 just needed changing to ext3 as wellYes.

If after the next reboot things get discombobulated you may have to go back into fstab and change the /dev/sdxy designation to UUID. The sdxy type of reference sometimes changes on reboot which is why the current method is to use UUID's instead. SO the sde1 line would change from this:
>                               /dev/sde1 /media/ecto1 [COLOR=Black]ext4[/COLOR]  defaults             0  0                      To this:
> UUID=d7901fed-2474-461d-806e-e93cc07b86ac  /media/ecto1 [COLOR=Black]ext4[/COLOR]  defaults             0  0It looks spookier but the UUID will never change unless you do a reformat.

As I recall pysdm doesn't know about UUID's but as you can probably tell I don't use it or think much of pysdm, mountmanager, ntfs-config, or any of the rest of these utilities :wink:

---

### Post by ischemic on 2011-05-11
Great, I'll change them to uids. Thanks again for all the help.

---

### Post by srs5694 on 2011-05-11
There's at least one other problem you should address, although it might not be having serious consequences right now, and it relates to one of your questions: As reported by Disk Utility, a "partition type" is a 1-byte code in the partition table that identifies the type of data to be stored on a partition, whereas a "type" is the actual filesystem or other data structure detected in the partition. Your /dev/sdd1 and /dev/sde1 both have partition type codes of 0x07, which is a code for NTFS or HPFS, whereas the filesystems detected in these partitions are ext3fs and ext4fs, respectively, both of which should have a type code of 0x83. You can correct this problem by using fdisk:


[list=1]
[*]Launch fdisk on the disk to be altered, as in "sudo fdisk /dev/sdd".
[*]Type "p" to verify you're working on the correct disk. If you're not, type "q" to exit without making any changes.
[*]Type "t" to change a type code. Since both disks have just one partition, fdisk will skip asking you for a partition number and ask for a type code. Enter "83".
[*]Type "p" to view the partition table again and verify the correct change was made. If something seems wrong, type "q" to exit without saving your changes.
[*]Type "w" to save your changes and exit.
[/list]


You'll need to run through this procedure twice, once for each disk.

The consequences of not fixing this problem are likely to be minor to nonexistent for a long time. Linux ignores partition type codes for most purposes, so you can go on using the computer just fine with the wrong type codes set. The catch is that if/when you try to use a utility that *does* rely on the partition type code, that utility will flake out in an unpredictable way. Some Linux installers rely on partition type codes, although I don't know offhand how Ubuntu's installer reacts to an improperly-set type code, so I can't say how Ubuntu specifically will respond if/when you try to upgrade or re-install like this. Windows relies on type codes, but I don't know offhand how it would react to this situation.

Overall, it's worth fixing this problem, but you shouldn't rush to do it so quickly that you're likely to make mistakes. Don't put it off forever, though; if you forget about it and then try to use a disk utility that relies on the type code, it might misbehave in an unpredictable way.

---

