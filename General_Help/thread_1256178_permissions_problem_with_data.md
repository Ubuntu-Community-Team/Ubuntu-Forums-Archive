---
title: "permissions problem with /data"
date: 2009-09-02
forum: General Help
---

### Post by ameyazing on 2009-09-02
Hi guys, I'm relatively new to Linux (I only know enuf to write code, compile and run it).

I'm facing a problem. I have kubuntu installed on my machine. I store all my data on /data partition. When I try to checkout code 4rm svn repository to a directory under /data, the operation fails giving an error 'Operation not permitted - failed to set permissions'. Works fine if I checkout the code into my home directory. /data partition is vfat.

I tried resolving the problem removing by removing umask and gid options for the partition from /etc/fstab. It didn't work.

Plz help me resolve this issue within the constraints:
1] /data partition has to remain vfat (needs to be accessed from windows as well)
2] want to checkout code into /data

Related Info:
$lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

$cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=2c28d8da-221e-458f-8461-f9ce26a7f668 /               ext3    relatime,errors=remount-ro 0       1
# /data was on /dev/sda6 during installation
UUID=88D9-F45B  /data           vfat    defaults,umask=007,gid=46 0       1
# /home was on /dev/sda5 during installation
UUID=385f5cf1-bff2-4737-a3b4-ec9fbebbcae9 /home           ext3    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=a2ab5470-0d92-4f63-a450-c56e22192916 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by paradigm2 on 2009-09-02
ls -l /data

What are the permissions and who is the owner of the /data partition?

---

### Post by StuartN on 2009-09-02
> **ameyazing said:**
> # /data was on /dev/sda6 during installation
UUID=88D9-F45B  /data           vfat    defaults,umask=007,gid=46 0       1


There are no owner attributes on the vfat volume so they are taken from the mount, which probably means they belong to root with this fstab entry. Adding the options uid=ameyazing,guid=ameyazing (no spaces between options) might sort it out.

---

### Post by ameyazing on 2009-09-03
Hi StuartN,
    I tried ur solution. I edited the file so that the entry in fstab now looks like
UUID=88D9-F45B  /data           vfat    defaults,umask=007,gid=46,uid=ameyazing,guid=ameyazing 0       1
then, did 'mount -a'. I think this will mount the filesystem again with new options. Even after this it did not work. I cud not checkout the code on that partition yet.

Paradigm,
One of the entries in ls -l /data is
drwxrwx--- 3 root plugdev 65536 2009-08-07 22:05 office

I don't know what all the fields in that line mean, but I think the owner must be root, rite?

---

