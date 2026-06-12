---
title: "trying to mount ntfs partitions at start"
date: 2010-03-19
forum: General Help
---

### Post by dmdevotee on 2010-03-19
i want to mount at kubuntu startup some ntfs drives

now, i have, on dolphin, to click the ntfs partitions to mount them

and after doing that, this lines are included on /etc/mtab

/dev/sda1 /media/WD10EADS fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdc3 /media/DATOS fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sde1 /media/IPOD_HD-1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/SAMSUNG\0401TB-1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdd2 /media/SEAGATE-1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

but when i add that lines to /etc/fstab and reboot, i can't access the ntfs drives. dolphin says than only "root" can mount /dev/sda1 on /media/WD10EADS (for example)

i tried this too:


/dev/sda1 /media/WD10EADS ntfs-3g rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdc3 /media/DATOS ntfs-3g rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sde1 /media/IPOD_HD-1 ntfs-3g rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/SAMSUNG\0401TB-1 ntfs-3g rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdd2 /media/SEAGATE-1 ntfs-3g rw,nosuid,nodev,allow_other,blksize=4096 0 0



can anyone explain what i'm doing wrong?

---

### Post by dmdevotee on 2010-03-19
if write this on console:

sudo mkdir WD10EADS
sudo mount -t ntfs-3g -o rw /dev/sda1 /media/WD10EADS

it works (but this is not what i want to do of course, i want to auto-mount at startup without typing the root pass).

---

### Post by dmdevotee on 2010-03-19
also i tried to make a script called script.sh:

#! /bin/bash
sudo mkdir /media/WD10EADS
sudo mount -t ntfs-3g -o rw /dev/sda1 /media/WD10EADS

and i did:

sudo chmod 777 script.sh

so it haves all permissions

i placed it on folders:

/home/dmdevotee/.kde/Autostart
/etc/init.d

but it won't work too

---

### Post by DawieS on 2010-03-19
If you are running 9.10 (Karmic), you will not get much joy by adding NTFS partitions to /etc/fstab. For a workable solution, please see [_**this**_]("http://ubuntuforums.org/showthread.php?t=1429790") thread.:grin:

---

### Post by dmdevotee on 2010-03-19
> **DawieS said:**
> If you are running 9.10 (Karmic), you will not get much joy by adding NTFS partitions to /etc/fstab. For a workable solution, please see [_**this**_]("http://ubuntuforums.org/showthread.php?t=1429790") thread.:grin:

you mean this?

> **DawieS said:**
> 
You can change the default disk behavior of Karmic by editing the following file using the '**sudo gedit**' command in a terminal:

/usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

To be able to mount disks without password authentication, look for the following header:

<action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">

under that will be something like this:

<defaults>
<allow_any>no</allow_any>
<allow_inactive>no</allow_inactive>
<allow_active>[COLOR=Red]auth_admin_keep[/COLOR]</allow_active>
</defaults>

change the highlighted one to:

<allow_active>[COLOR=Red]yes[/COLOR]</allow_active>

Save, exit and reboot. You should now be able to auto-mount your NTFS drives.

Notes:
- Please check whether you are enabled to **Mount user-space filesystems** in the **System - Administration - Users and Groups - Properties** tab.
- These changes may be overwritten by an upgrade and may require re-doing.
- From a security viewpoint, it is best to keep all drives unmounted when not required for service, especially while on the Internet. External drives should be switched off, to also prolong useful life.

I have Karmic running on three desktops in a home network, all with different hardware. I sometimes swap external drives between desktops, for super-fast file transfers. Since making these changes (and applying the 3 rules), I have found Karmic to be an absolute pleasure to work with!:grin::grin::grin:

it didn't work for me

by the way, with **Mount user-space filesystems** in the **System - Administration - Users and Groups - Properties** tab , do you mean "system preferences"?

[[IMG]http://img100.imageshack.us/img100/4644/instantnea1.png[/IMG]]("http://img100.imageshack.us/i/instantnea1.png/")


don't know where "properties" are

---

### Post by DawieS on 2010-03-19
Yes.

Ok, you are using a different version of Gnome.** Users and Groups** are under** System - Administration** on my version (Desktop 9.10)**.** If you select a user, the **Properties** tab is on the right.

---

### Post by dmdevotee on 2010-03-19
> **DawieS said:**
> Yes.

Ok, you are using a different version of Gnome.** Users and Groups** are under** System - Administration** on my version (Desktop 9.10)**.** If you select a user, the **Properties** tab is on the right.

i am using kde

i still can't see properties anywhere...i only see modify and nothing like [B]Mount user-space filesystems
[/B]

---

### Post by dmdevotee on 2010-03-19
i added this to etc/fstab

/dev/sdc3 /media/DATOS ntfs-3g defaults,locale=es_ES.utf8 0 0

that worked like a charm!

---

### Post by DawieS on 2010-03-19
Sorry, it looks like I took you on a wild goose chase for nothing. The **Mount user-space filesystems** toggle is probably somewhere in the system files. The problem is to find it.
[IMG]http://ubuntuforums.org/images/icons/icon11.gif[/IMG]

---

