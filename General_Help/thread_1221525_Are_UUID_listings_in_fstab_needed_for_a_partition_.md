---
title: "Are UUID listings in fstab needed for a partition to auto load to the desktop on boot"
date: 2009-07-23
forum: General Help
---

### Post by ozguitarplayer on 2009-07-23
Hi,
I have tried to get a partition the holds my personal files to load to the desktop when I boot into the o/s.
I have posted threads about this in the past and all the appreciated advice centers around /etc/fstab, and I have read in depth about fstab and followed the advice with little result.

Now I have come across UUID.
In fstab there are UUID listings for the swap partition and for CD drives, nothing else.
My question: Do I need to have an UUID entry for the partition as well as;

/dev/sda3    /media/niles    vfat    auto,user    0     0 
 
also; gparted formats to fat32 not vfat, yet I believe it's better to list the partition in fstab as vfat, is this correct?

---

### Post by Whiffle on 2009-07-23
UUID is just another way of identifying a partition.  The advantage of it is that if your drives change order (some BIOS's do this, what was sda when you installed might become sdb, or sometimes if you have a USB drive plugged in, it cases havoc), it still boots normally.

---

### Post by ozguitarplayer on 2009-07-24
Thanks Wiffle, I guess this means that I don't have to use the UUID for the particular drive I'm trying to auto mount on boot?

Here is my fstab file, (the /dev/sda3 is the one in question) from what I understand with this entry the drive should auto mount. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bf172516-e9bd-4055-a108-309f6a84922e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1b99b094-b670-4e1b-9e43-516f94c8b20b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3       /media/niles    vfat        user,auto            0       0

---

### Post by dcstar on 2009-07-24
> **ozguitarplayer said:**
> Thanks Wiffle, I guess this means that I don't have to use the UUID for the particular drive I'm trying to auto mount on boot?

Here is my fstab file, (the /dev/sda3 is the one in question) from what I understand with this entry the drive should auto mount. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bf172516-e9bd-4055-a108-309f6a84922e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1b99b094-b670-4e1b-9e43-516f94c8b20b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3       /media/niles    vfat        user,auto            0       0

Do not use /media as a mountpoint for internal drives, /media is a system folder meant for removable drives only.

```
sudo mkdir /whatever
``` will allow you to create a mountpoint that will not interfere or be affected by the system.

---

### Post by mcduck on 2009-07-24
> **dcstar said:**
> Do not use /media as a mountpoint for internal drives, /media is a system folder meant for removable drives only.

```
sudo mkdir /whatever
``` will allow you to create a mountpoint that will not interfere or be affected by the system.

It's absolutely OK to mount any drives, including internal ones, inside /media. And it definitely doesn't "interfere with the system" in any way. Actually that's exactly where the Ubuntu's installer will configure your extra drives to mount into. :)

The only thing to consider is that drives mounted in /media will appear in the desktop & the Places-menu, while drives mounted elsewhere (like inside /mnt which is the other standard location for mounting) will not appear anywhere.

Personally, I mount my internal drives inside /mnt as I don't want them to show on the desktop, but like I said there's absolutely no reason to not mount them in /media if you want the icons.

---

### Post by nikhilk on 2009-07-24
> **ozguitarplayer said:**
> Here is my fstab file, (the /dev/sda3 is the one in question) from what I understand with this entry the drive should auto mount.

Yes the entry looks OK and there should not be any problem while mounting that partition. Let us know if you face any problems while mounting.

---

### Post by ozguitarplayer on 2009-07-24
Thanks all...

dcstar...it's been a directory form a while now this is it in /media ls -l
  
drwx------ 6 nigel root 16384 1970-01-01 10:00 Niles

still doesn't mount
mounting issues don't have anything to do with permissions do they?

mcduck...I'll take note of that, but for the moment I need to have this one drive to mount on start up, and apart from that I want to learn how to control the mount issues.
However if I wanted to would I do it like this...sudo mkdir /mnt/filename?
If the drive was in /mnt and I mounted the drive manually would it then still appear on the desktop and would it appear in Nautilus file browser along with the other drives?  

nikhilk....I've been through this so many times that I am also sure that it is right, and I'm a novice, it's not that I can't mount the drive at all it that I can't get it to automount no start up.

---

### Post by subodh.rohilla on 2009-07-24
I found a link which has the solution of the same problem you are facing.

I think this can help you out : [http://ubuntuforums.org/showthread.php?t=449313](http://ubuntuforums.org/showthread.php?t=449313)

---

### Post by ozguitarplayer on 2009-07-24
thanks subodh.rohilla that sorted it. 
I hadn't tried using the defaults entry in fstyab as I had thought that part ot the defaults setting was noauto for mount on boot. 

When making a directory is upper case used if the drive name is uper case e.g. drive named Niles or should it be lower case?

---

### Post by nikhilk on 2009-07-24
> **ozguitarplayer said:**
> When making a directory is upper case used if the drive name is uper case e.g. drive named Niles or should it be lower case?

There is absolutely no relation between the name of the mount point and the label of the partition you want to mount.
You can mount to any directory say, /media/abc and it will still work fine.

---

### Post by ozguitarplayer on 2009-07-24
thanks however I don't understand, I thought the label was Niles then it would be /media/Niles, what else would I enter after /media/?

---

### Post by nikhilk on 2009-07-24
> **ozguitarplayer said:**
> thanks however I don't understand, I thought the label was Niles then it would be /media/Niles, what else would I enter after /media/?

I mean that there is no restriction on you that you MUST have the mount point /media/Niles to match the partition label. You can very well mount a partition with label xyz on say, /media/abc.
Of course, to keep things logical, most users will chose a mount point name that will help them map it to the drives seen in Windows.
e.g. If there is a D: drive in Windows with label "Games" a sensible mount point name can be /media/windows_D or /media/games, anything which is more logical to you.
What I am saying is, there is no compulsion that the mount point name MUST be letter-to-letter same as the partition label.

---

### Post by ozguitarplayer on 2009-07-24
got it, it's just a name
it's good to learn
thanks again

---

### Post by nikhilk on 2009-07-24
> **ozguitarplayer said:**
> got it, it's just a name
it's good to learn
thanks again

You are welcome :)

---

