---
title: "mount: only root can do that"
date: 2011-12-09
forum: General Help
---

### Post by Bromden on 2011-12-09
Hello, I've got problems mounting an external USB HDD on Ubuntu 10.10.
I know, there are a lot of solutions for this problem on the WEB but none of those is working...

If I mount with sudo like this:
mount /dev/sdb1 /media/Elements

everything works, but if I mount without using the terminal i get this:
mount: only root can mount /dev/sdb1 on /media/Elements

Currently this is the fstab configuration:
UUID=3AD8D1CDD8D18791    /media/Elements    ntfs-3g   
 defaults,locale=en_US.utf8   0    0

I've tried this command:
sudo chown root:MYUSER /media/Elements

but didn't worked.

What should I do?

---

### Post by editheraven on 2011-12-09
Try  sudo chown MYUSER:MYUSER /media/Elements

le : also try
```
mkdir /home/YOURUSERNAME/mount/usb && mount /dev/sdb1 /home/YOURUSERNAME/mount/usb
```

---

### Post by Bromden on 2011-12-09
Nope I always get
mount: only root can do that

---

### Post by Lars Noodén on 2011-12-09
Look at the [mount](http://manpages.ubuntu.com/manpages/oneiric/en/man8/mount.8.html) options [font=Courier New]user[/font], [font=Courier New]users[/font] and [font=Courier New]owner[/font].  They should let a non-root user mount the filesystem.

---

### Post by Bromden on 2011-12-09
Mmm, should i do that typing "mount" in terminal?

The output shows me the different filesystems with the current permissions, but sb1 doesn't appear in the list... :\

---

### Post by Lars Noodén on 2011-12-10
> **Bromden said:**
> Mmm, should i do that typing "mount" in terminal?

The output shows me the different filesystems with the current permissions, but sb1 doesn't appear in the list... :\

The options go in [/etc/fstab](http://manpages.ubuntu.com/manpages/precise/en/man5/fstab.5.html) where you have the other parameters for sb1.  It's best to identify the devices by UUID, though.

The output from [font=Courier New]mount[/font] will only show the partitions that are actually mounted and the options they were mounted with.  If you are still trying to mount sb1 then it won't show up on the list yet.

---

### Post by perperNorbi on 2011-12-10
According to the manual of ntfs-3g
"If  ntfs-3g is set setuid-root then non-root users will be also able to mount volumes."

so I think 
sudo chmod u+s `which ntfs-3g`
should solve your problem.

---

### Post by Lars Noodén on 2011-12-10
[/etc/fstab](http://manpages.ubuntu.com/manpages/precise/en/man5/fstab.5.html) could be modified like this:

```

UUID=3AD8D1CDD8D18791 /media/Elements ntfs-3g rw,nodev,exec,nosuid,noauto,owner,locale=en_US.utf8 0 0

```

The important options are [font=Courier New]rw[/font] and [font=Courier New]owner[/font].  I don't use or condone NTFS so I  don't know if the other options are supported, but it's something to start with.

---

### Post by Bromden on 2011-12-13
Ok I found the solution, and obviously it was already on this forum ^^

I found it here:
[http://ubuntuforums.org/showthread.php?t=872197]("http://ubuntuforums.org/showthread.php?t=872197")

Here my actual fstab configuration:
#Entry for /dev/sdb1 :
UUID=3AD8D1CDD8D18791	/media/Elements	ntfs	defaults,**auto,users,uid=1000,gid=1000**,nls=utf8,umask=0222	0	0

Thank you very much for the assistance!

---

