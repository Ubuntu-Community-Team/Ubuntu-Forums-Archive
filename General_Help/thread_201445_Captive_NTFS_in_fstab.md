---
title: "Captive NTFS in fstab"
date: 2006-06-21
forum: General Help
---

### Post by ouch on 2006-06-21
I'm having problems mounting my NTFS partitions automatically in my /etc/fstab file with captive ntfs. My fstab is:

[FONT="Fixedsys"] [SIZE="2"]/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               reiserfs defaults        0       1
/dev/hdc1       /boot           reiserfs notail          0       2
#/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222        0       0
#/dev/hda2       /media/hda2     ntfs    nls=utf8,umask=0222        0       0
#/dev/hdb1       /media/hdb1     ntfs    nls=utf8,umask=0222        0       0
/dev/hdc3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy1  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy2  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy3  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy4  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy5  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy6  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy7  auto    rw,user,noauto  0       0
/dev/hda2 /media/captive-games captive-ntfs defaults 0 0[/SIZE]
[/FONT]

I've two problems.

1. How do I enable write access for all users. Currently the filesystem mounts but on root can write files.
2. My fstab seems to hang the boot process. It stalls at the checking all filesystems stage. After a while booting shows the full boot log. At the bottom it has:

[FONT="Fixedsys"] 
 * Starting RAID devices...
 * Starting up LVM Volume Groups
Checking internal tree..finsihedblocks[18..8211]: 0 transactions replaye[ok]
[/FONT]
If it press CTRL-C I can continue boot. But would obviously like booting to complete normally.

Thanks

---

### Post by mlind on 2006-06-21
does umask=0222 mount parameter help?
nice set of floppy drives ;)

Captive ntfs may have some serious io issues though
[http://www.debian-administration.org/articles/367](http://www.debian-administration.org/articles/367)

---

### Post by ouch on 2006-06-22
Thanks, will try that when I get home this evening. Not sure what my crazy nonexistant floppy collection is about either.

And thanks for the additional info, shall give it a good read.

---

### Post by mlind on 2006-06-22
[QUOTE=ouch]Thanks, will try that when I get home this evening. Not sure what my crazy nonexistant floppy collection is about either.

And thanks for the additional info, shall give it a good read.[/QUOTE]

You can remove floppy1-floppy7 from fstab, those were caused by a bug that was
present on Dapper flight versions, but should have been fixed on final.

---

### Post by bforbes on 2006-06-22
If umask=0222 doesn't work you could try adding "gid=users" as an option of the mount, like this:
```

/dev/hda2 /media/captive-games captive-ntfs defaults,gid=users 0 0

```

I'm not sure but you might have to change "users" to its numerical value, which is indicated as the third field of the line starting with "users" in /etc/group. For brevity:
```

cat /etc/group | grep '^users' | cut -d ':' -f 3

```

---

### Post by ouch on 2006-06-22
Thanks for your input bforbes. I'll experiment over next evening or two.

---

### Post by mlind on 2006-06-22
new Dapper install uses group called 'plugdev' for this as default. My ntfs share
was automatically added by installer to /etc/fstab

```

/dev/sda5       /media/D     ntfs    ro,nls=utf8,umask=007,gid=46 0       0

```

where group id 46 belongs to plugdev.

---

