---
title: "Trouble mounting hard drive with fstab..."
date: 2010-08-27
forum: General Help
---

### Post by bobleny on 2010-08-27
I purchased a new hard drive, plugged it in, formated it, edited fstab to auto mount it, and though it is mounting the drive, it won't allow me write privileges. I can read the drive, but I need root access to write to it.

The drive giving me the issue is sdd1. The others, I have no problems with. I can read and write to those without a hitch.

Here is my fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5d0ed718-2719-4b28-a031-9ab10f9aa740 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sda2 /media/sda2 ext3 rw,auto 0 0
/dev/sdb1 /media/sdb1 ntfs rw,auto 0 0
/dev/sdc1 /media/sdc1 ntfs rw,auto 0 0
/dev/sdc2 /media/sdc2 ntfs rw,auto 0 0
/dev/sdd1 /media/sdd1 ext3 rw,user,auto 0 0

```

Can someone help me figure out what I am doing wrong please?

Thanks!

---

### Post by mendhak on 2010-08-27
I think you'll need to set permissions on that mount once and it should 'remember' the permissions.  

sudo chmod a+w /dev/sdd1

So run that, then try to write a file.  Works? Good.  Then reboot and try making another file.

---

### Post by Ozymandias_117 on 2010-08-27
The problem isn't fstab, it's how ext3 handles permissions. What you need to run is ```
sudo chown user:user -R /media/sdd1
```

replace "user" with your username.

---

### Post by bobleny on 2010-08-27
Ah, yes. Thank you both. I just barely remember changing the permissions using chmod before. After a restart, it does appear to remember the settings.

Thanks!

---

### Post by Grenage on 2010-08-27
I think you can also use the 'user' flag in fstab, to allow all users access.

---

### Post by bobleny on 2010-08-27
I had already tried that:
```
/dev/sdd1 /media/sdd1 ext3 rw,user,auto 0 0
```

---

### Post by dino99 on 2010-08-27
as im too lazy to tweak fstab and/or mtab, i use mountmanager to deal with partitions and devices, its a nice tool, try it

---

### Post by Ozymandias_117 on 2010-08-27
> **Grenage said:**
> I think you can also use the 'user' flag in fstab, to allow all users access.

That only refers to who can mount/unmount not access.

---

### Post by Grenage on 2010-08-27
> **Ozymandias_117 said:**
> That only refers to who can mount/unmount not access.

Ah; thank you for the clarification.

---

### Post by Morbius1 on 2010-08-27
Actually "user" in fstab without it's little brother "noauto" will not  allow a user to unmount the partition because the only "user" at the  time fstab is executed is root. You would need to use "users" in fstab  to allow anyone to unmount the partition.

Anyway , Did you try this:

> **Ozymandias_117 said:**
> The problem isn't fstab, it's how ext3 handles permissions. What you need to run is ```
sudo chown user:user -R /media/sdd1
```replace "user" with your username.

Mountmanager or no mountmanager, user or users, you're still going to have to change permissions or ownership.

[COLOR=Blue]EDIT:[/COLOR]
:p:p Didn't realize this was marked [SOLVED].
I keep forgetting to read the posts first then answer.

---

