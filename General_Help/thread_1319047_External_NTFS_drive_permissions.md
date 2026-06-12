---
title: "External NTFS drive permissions"
date: 2009-11-08
forum: General Help
---

### Post by nikogawa on 2009-11-08
I used to share some folders on my NTFS external hard drive through samba in Jaunty. Since I upgraded to Karmic, these shares no longer work.

It seems that the permissions for this drive are only set for myself (no permissions for group or others) and I can not change these permissions (not with chmod or with nautilus, they keep jumping back).

I would like to have the same permissions on my external drives as in jaunty (owned by root and writable, executable by everyone). Since I use several drives I would like to avoid using /etc/fstab.

I tried adding the key mount_options with [umask=000] in system/storage/default_options/ntfs . But this doesn't seem to work in Karmic. 

Where can I change the permissions on these automatically mounted devices.

Thank you,
Niko

---

### Post by nikogawa on 2009-11-08
It seems that these mount options are hard-coded in devicekit-disks.

However I have found a dirty hack which seems to work for me. I made the following script for my two external hard drives. It first unmounts the drives, and then mounts them again with dmask=000 as mount option.

```

#!/bin/bash

devkit-disks --unmount /dev/disk/by-uuid/BEDC44F4DC44A90B
devkit-disks --unmount /dev/disk/by-uuid/0D3594370C618A2A

devkit-disks --mount-options "dmask=000" --mount /dev/disk/by-uuid/BEDC44F4DC44A90B
devkit-disks --mount-options "dmask=000" --mount /dev/disk/by-uuid/0D3594370C618A2A

```


I am still looking for a solution to change the default mount options.

---

### Post by da3rX on 2009-11-10
I am having the exact same problem. Is there a better solution to this?

---

### Post by holtz on 2009-11-13
I have the exact same problem as well.  I'm going to file a bug.

We can't continue to have bugs like this in newly released versions if we want to get wider adoption of Ubuntu.  Do developers consider the affect that changing something like a mechanism will have for users?

Worse, nowhere can I find any information on how to change the default permissions for mounted USB drives.  Googling turns up any number of possiblities: HAL, UDEV, fstab, automount, gconf.  Which one does Ubuntu use?  I have no idea.  I really shouldn't have to know.  There are megabytes of help files but no where can I find the information I need.

---

### Post by holtz on 2009-11-13
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/482501](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/482501)

---

### Post by dunskii on 2009-11-22
just wondering if there has been any updates to this problem yet..?
Cheers
D

---

### Post by dunskii on 2009-11-23
Ok, well I have found a work around for this if you share over the network.
I just shared my drive with read write access for all using samba (i know this isnt the most secure but it worked)
Then just accessed the drive via places -> network from the other pc's
Only problem is you still cant access the drive on the pc it is plugged into unless you're in root.
Hope this helps someone.
D

---

### Post by mikeize on 2009-11-29
I see the bug is triaged in launchpad... this is driving me crazy.

---

### Post by wackyraces on 2009-12-07
I have the same problem. I upgraded from Jaunty to Karmic and lost the ability to share external NTFS formatted drives. 

I can confirm it is a permissions problem when the drive is auto-mounted by devkit-disks. Creating a shell script to unmount and remount the relevant drive with the right permissions (as suggested above) solved it for me, but it's not ideal.

If I find a way of modifying the default behavior of devkit-disks I post it here, however things don't look promising!

---

### Post by speedbacon on 2009-12-15
Thanks for filing a bug on this.  This is driving me crazy too!  Does anyone know if there is a workaround for this yet?

---

### Post by hoz74 on 2009-12-15
Hello i'm new here, and french so excuse my english ,

i follow the tip of nicogawa, and made a small script that you have to launch when you want to have full access on you external drive...


you just have to launch it, waiting for a solution from devs ...

maybe this can help someone ?

see you

---

### Post by merindol on 2010-04-29
> **nikogawa said:**
> 
```

#!/bin/bash
devkit-disks --unmount /dev/disk/by-uuid/BEDC44F4DC44A90B

```


On Ubuntu Lucid (10.4) the devkit-disks command has been replaced by /usr/bin/udisks

---

### Post by speedbacon on 2010-05-11
Thanks for this information!

---

### Post by danroy on 2010-12-08
Download the sources via apt-get

```

mkdir udisks
cd udisks
apt-get source udisks

```

Modify src/device.c

```

cd udisks-1.0.1+git20100614
gedit src/device.c

```

Line 5878: Change default dmask and fmask to whatever you desire:

```

/* ---------------------- ntfs -------------------- */
/* this is assuming that ntfs-3g is used */

static const char *ntfs_defaults[] = { "uid=", "gid=", "dmask=0000", /*"fmask=0111",*/ NULL };
static const char *ntfs_allow[] = { "umask=", "dmask=", "fmask=", NULL };

```

Build and install

```

sudo apt-get build-dep udisks
debuild
cd ..
sudo dpkg -i udisks_1.0.1+git20100614*.deb

```

To go back

```

apt-get install --reinstall udisks

```

---

