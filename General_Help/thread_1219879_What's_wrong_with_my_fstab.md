---
title: "What's wrong with my fstab?"
date: 2009-07-22
forum: General Help
---

### Post by dwally89 on 2009-07-22
Hi,

My fstab currently looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=3aad6846-9c94-48f6-8c6a-990f60ae480f /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=329325d9-0726-434c-8601-b5f96e38ff3d /home           ext3    relatime        0       2
# /media/Data was on /dev/sda2 during installation
UUID=0AECF7027E340363 /media/Data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /media/sda1 was on /dev/sda1 during installation
UUID=07D7-041A  /media/sda1     vfat    utf8,umask=007,gid=46 0       1
# /media/sda5 was on /dev/sda5 during installation
UUID=fb92bf5b-50be-48e9-b3cc-c59b40688595 /media/sda5     ext3    relatime noauto       0       2
# /media/sda7 was on /dev/sda7 during installation
UUID=533943e1-7689-486c-beae-7c00a5520700 /media/sda7     ext3    relatime noauto       0       2
# /media/sda8 was on /dev/sda8 during installation
UUID=C8E9-A608  /media/sda8     vfat    utf8,umask=007,gid=46 noauto 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

But when I try and mount sda5, sda7, or sda8, it comes up with an error. I added in the "noauto" option myself, but I'm assuming I put it in the wrong place, or used the wrong syntax.

What do I need to do to fix it?

Thanks

---

### Post by nikhilk on 2009-07-22
> **dwally89 said:**
> Hi,

My fstab currently looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=3aad6846-9c94-48f6-8c6a-990f60ae480f /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=329325d9-0726-434c-8601-b5f96e38ff3d /home           ext3    relatime        0       2
# /media/Data was on /dev/sda2 during installation
UUID=0AECF7027E340363 /media/Data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /media/sda1 was on /dev/sda1 during installation
UUID=07D7-041A  /media/sda1     vfat    utf8,umask=007,gid=46 0       1
# /media/sda5 was on /dev/sda5 during installation
UUID=fb92bf5b-50be-48e9-b3cc-c59b40688595 /media/sda5     ext3    relatime noauto       0       2
# /media/sda7 was on /dev/sda7 during installation
UUID=533943e1-7689-486c-beae-7c00a5520700 /media/sda7     ext3    relatime noauto       0       2
# /media/sda8 was on /dev/sda8 during installation
UUID=C8E9-A608  /media/sda8     vfat    utf8,umask=007,gid=46 noauto 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

But when I try and mount sda5, sda7, or sda8, it comes up with an error. I added in the "noauto" option myself, but I'm assuming I put it in the wrong place, or used the wrong syntax.

What do I need to do to fix it?

Thanks

Did you changes something recently? I mean were things OK before you are facing problems mounting now? Or have you created new partitions?

---

### Post by dwally89 on 2009-07-22
> I added in the "noauto" option myself, but I'm assuming I put it in the wrong place, or used the wrong syntax.
.

---

### Post by Cheesemill on 2009-07-22
It think it should be:
```
relatime,noauto
```

---

### Post by dwally89 on 2009-07-22
Thanks. One problem now though, they will only mount with sudo. How do I change the permissions so they'll mount with a normal user?

Thanks

---

### Post by nikhilk on 2009-07-22
> **dwally89 said:**
> I added in the "noauto" option myself, but I'm assuming I put it in the wrong place, or used the wrong syntax.

OK, I thought that was something you were trying out to resolve some other mounting related problem :)
As Cheesemill said all the options should be separated by commas. Separating with a space has a different meaning. You can take a look at the [this]("http://www.tuxfiles.org/linuxhelp/fstab.html") for details on the structure of /etc/fstab file.

---

### Post by dwally89 on 2009-07-22
> **dwally89 said:**
> Thanks. One problem now though, they will only mount with sudo. How do I change the permissions so they'll mount with a normal user?

Thanks.

---

### Post by nikhilk on 2009-07-22
> **dwally89 said:**
> Thanks. One problem now though, they will only mount with sudo. How do I change the permissions so they'll mount with a normal user?

Add either user or users to the options list after noauto to allow normal users to mount/unmount.

e.g.
```
UUID=fb92bf5b-50be-48e9-b3cc-c59b40688595 /media/sda5     ext3    users,relatime,noauto 0 2
```

---

### Post by dwally89 on 2009-07-22
Thanks, all working now :-)

---

### Post by nikhilk on 2009-07-22
> **dwally89 said:**
> Thanks, all working now :-)

Glad to help!

---

