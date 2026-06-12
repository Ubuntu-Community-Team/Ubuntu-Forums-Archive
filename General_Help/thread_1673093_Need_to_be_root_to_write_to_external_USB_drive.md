---
title: "Need to be root to write to external USB drive"
date: 2011-01-21
forum: General Help
---

### Post by klaasvg on 2011-01-21
Hi,
I have a problem accessing one of my external drives. When I plug in the device, it is recognized and mounted probery and I can read from it.
But it is impossible to write to it, unless I use root (sudo) rights.
In the past I could just access this drive.
Using lsscsi shows that the drive is regocnized as device /dev/sdh, issuing the mount command shows that it is mounted to the /media/BACKUP directory, which correctly appears on the desktop as a USB icon.
The drive is formatted as type ext3
But is remains a mystery why I need root access to write to it. Using antoher USB stick (type vfat) does not have the problem.

It seems to be a permission problem: see the output below. It is de BACKUP drive that can only be accessed as root, and indeed are user owner and group owner of the mounted directory set to root for this drive...
How can this be changed without doing this manually each time?

klaas@ubuntu-desktop:~$ cd /media
klaas@ubuntu-desktop:/media$ ls -l
total 20
drwxr-xr-x 19 root  root   4096 2010-08-14 22:03 BACKUP
drwx------ 10 klaas klaas 16384 2011-01-22 03:45 LEXAR128
klaas@ubuntu-desktop:/media$ 


TIA, Klaas

---

### Post by earthmeLon on 2011-01-21
After you insert the problematic drive, what is the output of:

```
ls -lh /media/
```

---

### Post by klaasvg on 2011-01-21
LOL in a cross-post I added this missing info! :)

---

### Post by earthmeLon on 2011-01-21
> **klaasvg said:**
> LOL in a cross-post I added this missing info! :)

Post it here next chance you get.  Hopefully it's a simple permissions issue :D

---

### Post by klaasvg on 2011-01-22
Excuse me, I mean I posted it simultaeously with your post on this very thread, I edited my original message by adding this info.
Indeed I guess this is not the same as cross posting :oops: 
But ths info is in my first message, it appears it is a permission issue indeed but solving it is the next step... So tips are still welcome :)

---

### Post by tredegar on 2011-01-22
**sudo chmod 777 /media/BACKUP**
will fix up the permissions for you.

---

### Post by klaasvg on 2011-01-22
OK this works, at least for the time being. I have unplugged and replugged again the drive and it appears that the 777 permissions are persisted!
My question: were is this saved? On the external drive or on my machine?
And what determines the user/group owner of the drive, the other (Lexar) driver has myself (klaas) as owner and therefore does not have the problem.
But the major question remains: what determines the user/group owner AND the permissions for a mounted drive and were is this saved per drive?

---

### Post by tredegar on 2011-01-22
> But the major question remains: what determines the user/group owner AND the permissions for a mounted drive and were is this saved per drive?
The permissions, GID and UID for the mountpoint determine this for drives mounted with a linux filesystem.

You create a file to be the mountpoint.
You assign appropriate permissions, GID and UID to that mountpoint.
Then you mount the partition to that file. The filesystem will (sensibly) inherit these permissions from its mountpoint.

Or you can set it all up in **/etc/fstab**
Or even with a udev rule.

> And what determines the user/group owner of the drive, the other (Lexar) driver has myself (klaas) as owner and therefore does not have the problem.

The Lexar has a windows filesystem I think. Windows filesystem "permissions" are a nightmare, and I'd rather not go there, but when mounting windows partitions like this, linux just assigns everything to you, because it doesn't have any information from the (stupid) windows filesystem to decide better.

---

### Post by earthmeLon on 2011-01-24
> **tredegar said:**
> The permissions, GID and UID for the mountpoint determine this for drives mounted with a linux filesystem.

You create a file to be the mountpoint.
You assign appropriate permissions, GID and UID to that mountpoint.
Then you mount the partition to that file. The filesystem will (sensibly) inherit these permissions from its mountpoint.

Or you can set it all up in **/etc/fstab**
Or even with a udev rule.



The Lexar has a windows filesystem I think. Windows filesystem "permissions" are a nightmare, and I'd rather not go there, but when mounting windows partitions like this, linux just assigns everything to you, because it doesn't have any information from the (stupid) windows filesystem to decide better.

Installing FUSE to allow non-root users to mount drives may help.  This way, you can set your fstab up so that whoever mounts the drive 'owns' it.  Just make sure you add the users you want to be able to mount to the 'fuse' group.

Edit: FUSE requires a reboot to work correctly

---

### Post by Claus7 on 2011-01-24
Hello,

I step in pretty quickly just to add this, type:

```
sudo chown (user name) /media/(name of partition)
and
sudo chgrp (user name) /media/(name of partition)
```

and see what you get the next time you mount the drive.

Just change the (user name) with that you 've got on your pc, without using the parentheses ...

Regards!

---

### Post by earthmeLon on 2011-01-24
> **Claus7 said:**
> Hello,

I step in pretty quickly just to add this, type:

```
sudo chown (user name) /media/(name of partition)
and
sudo chgrp (user name) /media/(name of partition)
```

and see what you get the next time you mount the drive.

Just change the (user name) with that you 've got on your pc, without using the parentheses ...

Regards!

This is a solution.  I wouldn't recommend this as I use Linux because it allows me to set up my computer to work how I prefer it to do so.  

Whenever you plugin a thumb drive, you want to be able to modify the files and not have to mess around with the command prompt.  There should be a way to set up your system to do this.

Whenever I plug in a thumb drive, Ubuntu creates /media/WHATEVER at that time.  /media/WHATEVER is removed when the thumb drive is removed.  I would suggest getting your system set up so that when you plug in new drives, it is smart enough to assign it to your user to prevent issues.

---

### Post by Claus7 on 2011-01-24
Hello,

> **earthmeLon said:**
> This is a solution.  I wouldn't recommend this as I use Linux because it allows me to set up my computer to work how I prefer it to do so.  

Whenever you plugin a thumb drive, you want to be able to modify the files and not have to mess around with the command prompt.  There should be a way to set up your system to do this.

Whenever I plug in a thumb drive, Ubuntu creates /media/WHATEVER at that time.  /media/WHATEVER is removed when the thumb drive is removed.  I would suggest getting your system set up so that when you plug in new drives, it is smart enough to assign it to your user to prevent issues.

I do get this issue every time, while formatting a new drive from command line, so in the end (and only once) I have to type those commands. After that the drive is ready to be used without any problem and on any computer. I thought that this might solve the problem the OP is facing permanently, by sharing my experience. I do not know why the OP is facing this problem in the first place, yet these commands will make no harm on the drive if tested.

Regards!

---

### Post by klaasvg on 2011-01-24
So it appears that there are 2 mthods to make the USB drive write-accessable by myself as user:
1. Giving the drive 777 access, so RWX permissions for everyone, although the drive is still mounted as root user/group owner.
2. Mounting the drive not as root but as the current user.

Both approaches will work. But I tend to believe that option 2 is conceptually the better one. 

It appears that BOTH the permissions and owner settings are preserved when disconnecting and reconnecting the drive. When I plugin another ext3 drive, is is again mounted as root, but when pluggin in the drive wich the changed settings, this is mounted as klaas.klaas with the changed permissions!

So somehow these settings are indeed preserved on a per-drive base. Where is this accomplished? I do not see any settings in the /etc/fstab file:

klaas@ubuntu-desktop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=f40e1519-1800-4f04-88df-87f085464ccb /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=6592b83e-1aa4-448a-beee-7608020693ec none            swap    sw              0       0
klaas@ubuntu-desktop:~$ 

So changing the permissions and/or owner for a particualr external drive works and is persisted, but my final question is HOW and WHERE this is persisted!
Any more hints?

---

### Post by Claus7 on 2011-01-26
Hello,

first of just to say that I did not mess with fstab almost with any of my ubuntu installations, and I did not face any problem with permissions with any external hdd I got and used with ubu.

Just to ask in order to verify:
are you sure that the formatting method you used, did not cause all the disks you have to be owned by root? 

I say so, cause during my humble experience, all the hdds come formatted either as fat(16 or 32) or ntfs, which means that if you want a linux compatible usb hdd, then you should format it to something like ext2, ext3 or ext4. So, do we know how did you do it? If I recall correctly, also gparted partition editor does this (giving root ownership), yet not be absolutely certain.

Why is bad your hdd to have user ownership? You refer to it like a compromise (sorry if I got it wrong). For me its how it should be, just not to have problems with root and the like, as you say you are facing...  

Also, from the fstab you are providing, at least me, cannot make any judgements, as it refers to sd**a** hard disk, which, from my humble experience, is the main disk you are using and not an external hdd. 

As a result, if you have a clean installation of ubuntu, you have not messed with fstab, and you plug in an external hdd, since it has root ownership, you change that to user, make it permanent, and you are ok.

Just some thoughts of what I can get with the information you provide,
hope I gave some insight,
Regards!

---

### Post by klaasvg on 2011-01-26
I say so, cause during my humble experience, all the hdds come formatted either as fat(16 or 32) or ntfs, which means that if you want a linux compatible usb hdd, then you should format it to something like ext2, ext3 or ext4. So, do we know how did you do it? If I recall correctly, also gparted partition editor does this (giving root ownership), yet not be absolutely certain.
*Yes my external disks were formatted as ext2 or ext3. Except for the Lexar disk.*


Why is bad your hdd to have user ownership? You refer to it like a compromise (sorry if I got it wrong). For me its how it should be, just not to have problems with root and the like, as you say you are facing...  
[I]I do not say it is bad, I just ask what is the better solution. And I agree with you that mounting the drive with user ownership is probably better.
[/I]
Also, from the fstab you are providing, at least me, cannot make any judgements, as it refers to sd**a** hard disk, which, from my humble experience, is the main disk you are using and not an external hdd. 

As a result, if you have a clean installation of ubuntu, you have not messed with fstab, and you plug in an external hdd, since it has root ownership, **you change that to user, make it permanent, and you are ok**.
[I]That is exactly what I did and what works. Nut my remainign question is how and were does the system persist that a given external drive is mounted with user ownership? Just to increase my knowledge and understanding. Because the mount directory /media/BACKUP is deleted and recreated each time when unplugging and replugging the disk, somewhere this information must be saved. And I miss the point where this happens!
[/I]

---

### Post by Claus7 on 2011-01-26
Hello,

glad things are getting clearer...
Now
> **klaasvg said:**
> Nut my remainign question is how and were does the system persist that a given external drive is mounted with user ownership? Just to increase my knowledge and understanding. Because the mount directory /media/BACKUP is deleted and recreated each time when unplugging and replugging the disk, somewhere this information must be saved. And I miss the point where this happens!
[/I]

I think that this can be done with fstab (at least one option), which you can tweak, yet I do not recommend (fstab in google will give you a lot of information). If you do so, you will say to it how to mount an external hdd, with different options from the defaults.

Happy ubuntuing and experimenting
(yet have in mind that messing with these, you might mess your installation, so be careful!),
Regards!

---

### Post by klaasvg on 2011-01-26
Thanx, but I do not need to tweak my fstab because the drive already works OK, the owner info is already saved because unplugging and replugging appears to maintain the earlier modified owner info. But I do not understand how it is saved... On the drive or on the system? Probably I miss somering trivial...

---

### Post by Claus7 on 2011-01-26
Hello,

> **klaasvg said:**
> Thanx, but I do not need to tweak my fstab because the drive already works OK, the owner info is already saved because unplugging and replugging appears to maintain the earlier modified owner info. But I do not understand how it is saved... On the drive or on the system? Probably I miss somering trivial...

I think both on the drive and on the system. From fstab I think that you can say the drive to be mounted with defaults or specific ownership. So, the driver itself has the info, yet the system has its own way of mounting devices. This is what I can get...
Someone with better experience might be able to help you better.

Regards!

---

### Post by leona on 2011-02-04
This exact issue was driving me crazy last night.
I bought a new external hard drive to create backups.
I formatted it to Ext3 via Gparted and then tried to make my backups.
I was unable to create directories or files, why? Because it mounted as ROOT, agggrrrhhh!!!
Spent all night searching forums for the answer, but the best thing I could come up with was placing a line in the fstab file, manually creating the directory in /media and ensuring 'users' was the group owner (I didn't think to chmod it to 777 d'oh!).
But, way oh way oh way, is it so difficult? Why can we not just plug in an external USB drive and for it just to work! I don't want to care or know about permissions, I want to just be able to plug a drive in, and use it, that's pretty basic functionality isn't it?
It should be able to detect the drive, mount it as the signed in user, done, easy. (seems easy to me anyway), so way doesn't Ubuntu do that?

There seems 1000 of threads of this nature, so this is a common problem, so why has this not been addressed?  Its about time it was fixed.

---

### Post by kukker32 on 2011-02-04
what i would do is type sudo nautilus into terminal, and locate the mounted usb and select permmissions under properties and then set the rights..

---

### Post by klaasvg on 2011-02-04
Locating the mounted directory and editing the rights, whether from the console or from Nautilus, defintately works and the new rights even appear to be saved SOMEWHERE (AFAIC not in fstab) because the next time you plug in the same drive, the /media/DRIVENAME directoy has the same rights and therefore is accessible.
But my still remaining questing is how and where this is preserved, because the mounted directory is destroyed and re-created each time.

---

### Post by Claus7 on 2011-02-04
Hello,

if I remember correctly, this has been discussed before and the conclusion was something like security issues. Since with just two commands, things are ok, I do not think that this is a big fuss. After all ubuntu and linux in general are supposed to be more (operating systems) secure than others.

Regards!

---

### Post by coffeecat on 2011-02-04
> **klaasvg said:**
> But my still remaining questing is how and where this is preserved, because the mounted directory is destroyed and re-created each time.

The ownership (created by chown) and permissions (created by chmod) are actually stored in the root of the filesystem and are retained, as you have discovered, when you remount the partition, or rather when you allow the system to automount the partition on an occasion subsequent to when you did the chown and chmod.

I must admit I've only glanced over the thread but I see the subject of /etc/fstab came up. You can set  permissions options in fstab but this might complicate the issue if you have already chown-ed and chmod-ed a partition. If I want a partition to be mounted by means of fstab, I prefer to chown and chmod the ownership and permissions that I want, and then simply use the 'defaults' option in the fstab line.

One interesting thing you'll notice is that if you set up a permanent mountpoint for an internal drive, mount it with 'sudo mount /dev/sdXY /media/mountpoint', then 'sudo chown yourusername: /media/mountpoint', you appear to be chown-ing the mountpoint. And, indeed, if you do a 'ls -l /media/' this appears to be so. But unmount the chown-ed partition and repeat the 'ls -l /media/' and you'll see that the mountpoint is still owned by root. This shows that the chown command (and chmod) act on the fileysytem itself, not on the mountpoint.

There's some discussion in this thread:

[http://ubuntuforums.org/showthread.php?t=1658937](http://ubuntuforums.org/showthread.php?t=1658937)

See my posts #7 and #12 for more of the same.

---

