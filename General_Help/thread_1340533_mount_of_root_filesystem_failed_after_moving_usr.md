---
title: "mount of root filesystem failed after moving /usr"
date: 2009-11-28
forum: General Help
---

### Post by sad1sm0 on 2009-11-28
I have a 500GB SATA drive, partitioned like so:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13         985     7815622+  83  Linux
/dev/sda3             986       25300   195310237+  83  Linux
/dev/sda4           25301       60801   285161782+   5  Extended
/dev/sda5           25301       37458    97659103+  83  Linux
/dev/sda6           37459       38431     7815591   83  Linux
/dev/sda7           60218       60801     4690948+  82  Linux swap / Solaris
/dev/sda8           38432       42078    29294496   83  Linux
/dev/sda9           42079       60217   145701486   83  Linux

```my fstab looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>             <mount point>   <type>  <options>           <dump>  <pass>
proc                        /proc           proc    defaults            0       0
# / was on /dev/sda2 during installation
UUID=eaa997bb-7df3-4203-80c6-172f432c0266 /               ext4    errors=remount-ro     0       1
# /boot was on /dev/sda1 during installation
UUID=fa856cf7-4933-4ccf-b946-3c0b3a3904f4 /boot           ext4    defaults            0       2
# /home was on /dev/sda3 during installation
UUID=cd4d8d4d-9190-464a-9a32-e523797777d2 /home           ext3    defaults            0       2
# swap was on /dev/sda7 during installation
UUID=7e16d328-c645-4bdd-b737-5a0c0320b0d8 none            swap    sw                  0       0

#CDROM
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8             0       0

# Shared Data (Media, Photos, Etc)
UUID=7dd932c4-2e7e-4db7-95ad-676a4be29c47 /share    ext3    defaults        0    2

```During the install, I opted for /boot / and /home to be on there own partitions.  I usually also have /opt /var and /usr on there own partitions, thus the reason for so many partitions.  I didn't do that with intrepid or karmic, but for some reason, karmic is complaining about the root being full.  My solution was of course to migrate /usr which was taking up a whopping 5.1GB of my 8 for /.  Anyway, I booted from a karmic usb disk and used tar to move the files to /dev/sda5 like so

```

$sudo su -
$(cd /media/root/usr; tar -cf - .) | (cd /mnt; tar -xf -)

```and added the following to my fstab

```

#/usr on /dev/sda5
UUID=794b3d4b-498e-4f47-9b69-b20cd153bea1 /usr          ext4      defaults        0    1

```last but not least
```

mv /media/root/usr /media/root/usr.old;mkdir /media/root/usr

```checked that the file perms were the same and all should have worked.  But
when I restarted, I was dropped to a maintenance shell with a warning saying that the root filesystem failed to mount.  I ls'd /usr and it was empty.  so I reversed the /usr.old back to /usr and commented out the fstab entry and got booted back up, but I still have the same disk space issue and need to resolve it without reinstalling.  I know that the uuid is pointing to the right drive and that it is mountable, because if I try to mount the partition somewhere else using fstab (for example inside of my home directory) it shows up no problem.  The filesystem is ext4, but I tried mounting in ext3 to see if that would work, and it didn't.  I used UUID and confirmed thru ls -l /dev/disk/by-uuid that it is mapping to /dev/sda5.  Any help on this would be greatly appreciated.

---

### Post by seeker5528 on 2009-11-28
Did the disk actually fill up or did you get warning in time to do something about it before you ran completely out of space?

The complaint about failing to mount the root partition would seem to me to be more significant than /usr being empty when you looked at it. It seems reasonable to think if there was a problem while mounting the root partition, it might not mount the rest of the partitions.

This could be resulting from the disk filling up or something that happened while you were moving files around.

I would suggest booting from your USB drive and doing fsck from there, if the partition is totally full this could lead to further difficulties if there are things that need to be fixed, so if that is the case you may want to move the files from /usr before running fsck.

Assuming you had warning before the disk totally filled up, my normal tendency would be to do things in steps.

First copy everything from /usr to the parition you want to mount at /usr, my personal preference would be something like

```
sudo cp -a /usr/* /some/partition
```

then edit the fstab file so that partition will be mounted at /usr. Then reboot to make sure that A: the partition is being mounted as expected and B: everything seems to be working. Then boot from your Karmic USB disk and delete the stuff from /usr.

I don't try to get that fancy with my partitioning, to me it is more trouble than it is worth. Also have not had many of these types of problems to deal with in recent history and have not kept up on what  additional potential risks there might be with ext4, so if anybody else is willing to chime in, please do so.

Later, Seeker

---

### Post by sad1sm0 on 2009-11-28
> **seeker5528 said:**
> Did the disk actually fill up or did you get warning in time to do something about it before you ran completely out of space?

When the warning first started showing up, I want to say I had over 200MB left, but now I'm down to 35MB so it's becoming a pressing issue.  I'm not totally sure where the 150+ mb has gone, but it seems like it's in /usr so it's probably programs I installed (forgetful sometimes).

> **seeker5528 said:**
> 
The complaint about failing to mount the root partition would seem to me to be more significant than /usr being empty when you looked at it. It seems reasonable to think if there was a problem while mounting the root partition, it might not mount the rest of the partitions.

This could be resulting from the disk filling up or something that happened while you were moving files around.

When it "fails to mount root filesystem", it's mounting the root partition, all of the files that are on /dev/sda2 are mounted, just not /home and /usr which are mounted after it's failed.  and when I move /usr.old back to /usr and revert to my old fstab it works again with no errors.  And, when I put the same partition in fstab mounting on a non 
root mount point, it boots fine and mounts the partition without a hitch.

> **seeker5528 said:**
> 
Assuming you had warning before the disk totally filled up, my normal tendency would be to do things in steps.


First copy everything from /usr to the parition you want to mount at /usr, my personal preference would be something like

```
sudo cp -a /usr/* /some/partition
```

then edit the fstab file so that partition will be mounted at /usr. Then reboot to make sure that A: the partition is being mounted as expected and B: everything seems to be working. Then boot from your Karmic USB disk and delete the stuff from /usr.


Other than using tar instead of cp -a this is the exact series of steps I took except that I also moved the files from /usr to /usr.old and created a new /usr with the same file permissions so that I wasn't trying to mount a filesystem in a non-empty folder.  When I went to boot back up, that's when the problem with not being able to mount the root filesystem showed up.

> **seeker5528 said:**
> 
I don't try to get that fancy with my partitioning, to me it is more trouble than it is worth. Also have not had many of these types of problems to deal with in recent history and have not kept up on what  additional potential risks there might be with ext4, so if anybody else is willing to chime in, please do so.

Well like I said, I used to do separate partitions from the install for /var, /usr, and /opt, but last couple of times I just did /boot, /, and /home which I've heard is pretty common.  However, this ability is something that I love about linux.  I just got karmic running the way I want and I don't feel like re-installing just to get more storage, when I should be able to just move /usr to a new partition and voila, an extra 100GB for /usr and 5GB for / which would keep that warning from popping up every time I (or any other user for that matter) logs in.  This issue only showed up with karmic even though the same programs are installed on the same partitions as intrepid.  There's an option to ignore, but that's not really an optimum solution since I am really close to filling up and running into problems.

I tried to use ext3 to mount the partitions, which I've read is possible, but that didn't make a difference.  I don't really understand the differences between ext3 and 4, but 4 sounded like a better option for fresh install.

---

### Post by seeker5528 on 2009-11-29
One thing I notice:

```
#/usr on /dev/sda5
UUID=794b3d4b-498e-4f47-9b69-b20cd153bea1 /usr          ext4      defaults        0    1
```

According to this:

[http://wiki.archlinux.org/index.php/Fstab](http://wiki.archlinux.org/index.php/Fstab)

: only the root partition should have a 1 in the pass column, so it gets the highest priority when checking, all other should have a 0 if you don't want them checked or a 2 so they are checked after the root partition.

I wouldn't think that would cause a problem, but I don't know what else it could be, from everything you described it sounds like it should have worked.

Later, Seeker

---

### Post by sad1sm0 on 2009-11-29
Yeah I can't ever remember what value to put there.  I changed it from 1 to 2 a couple of times.  I'll keep it at 2 now.  It doesn't seem to help.  I've tried using the /dev/sd** and LABEL= ways to reference the device as well and nothing has worked when mounting to /usr, but all work when mounting else where.

---

### Post by sad1sm0 on 2009-11-30
I'm not particularly sure what happened, but i modified the menu.lst file to boot into recovery mode and I'm running the new partition now.  I'd love to figure out what actually happened to cause this so any input is appreciated.

---

