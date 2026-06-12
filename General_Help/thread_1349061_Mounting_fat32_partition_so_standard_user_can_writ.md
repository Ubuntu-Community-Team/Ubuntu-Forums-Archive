---
title: "Mounting fat32 partition so standard user can write to it"
date: 2009-12-07
forum: General Help
---

### Post by beastrace91 on 2009-12-07
Hey All,

I was wondering if someone could post up an example fstab of how I would have it auto-mount my /dev/sda6 partition (thats fat32) so my default user can write to it.

Much Thanks,
~Jeff

---

### Post by leonardo_neo on 2009-12-07
First make a copy of your fstab, so that in case something goes wrong, you can get your default setting.

Now make a directory in the name of your fat32 partition. For example, I named my fat32 partition as common

> sudo mkdir /media/common

Then edit your fstab.....

> sudo gedit /etc/fstab

In the bottom of your fstab, add the following line....

> /dev/sda6 /media/common vfat umask=0000 0 0 

Note: Since my fat32 partition was named 'common' so in the line I named it common, if you have some other name, then replace 'common' with your 'fat32 partition name'. After you add the line, your etc/fstab should look something like this.....

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=bb50e7dd-9bdc-4836-bbf1-4290dde33b7e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1868fa8c-cebc-47bb-b210-23778c81b170 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda6 /media/common vfat umask=0000 0 0 

Save and exit.

Restart system.

I hope this should work.

---

### Post by beastrace91 on 2009-12-07
Ahhh excellent - the umask=0000 was the bit I was missing, I already had the rest of the fstab entry beyond that :)

So if I understand it correctly - setting the umask to 0000 makes it so all users can read/write to it as though root?

Cheers,
~Jeff

---

