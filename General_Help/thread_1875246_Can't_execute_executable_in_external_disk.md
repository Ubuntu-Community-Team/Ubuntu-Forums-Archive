---
title: "Can't execute executable in external disk"
date: 2011-11-04
forum: General Help
---

### Post by carcarah on 2011-11-04
Dear members,

i've been searching for a while about this problem, but with no success.

I was ubuntu 10.04 user, and used to execute executables directly from my fat external disk.

But in ubuntu 11.04 I can't. Even changing settings with chmod and so on.

The only way I can execute is putting the executable in linux partition.

Do you know how to solve this problem?

Thank you.

---

### Post by hwttdz on 2011-11-04
Sounds like you have the noexec in your mount options, how are you mounting the drive? Is it in your fstab?

---

### Post by Morbius1 on 2011-11-04
When you say executable are you referring to a Linux file that you want to execute? If you do then hwttdz looks like he's going down the right path.

But if you mean executable as in a Windows *.exe file - as in WIne - there may be way around this dilemma. Ubuntu changed the way fat and ntfs mounts automatically in that all files are now set as not executable. But if this is a Wine issue you can fix this. Please note I'm doing this from memory since I no longer have Wine installed on any of my systems.

Open Nautilus as root:
```
gksu nautilus
```And go to /usr/share/applications. Right click on "Wine Windows Program Loader" > Properties and in the command section you should see this:
> cautious-launcher %f wine start /unixRemove the "cautious-launcher %f" part of it so that it looks like this:
> wine start /unixNow when you double click an exe file you won't get that insane error message that it's not executable. Wine doesn't care nor can it determine if a given file has a Linux executable bit set. It's cautious-launcher that's getting in your way.

Note: There used to be an easier way to do this by creating your own file association but you would have to upgrade to Xubuntu to have that functionality today.

---

### Post by carcarah on 2011-11-06
Dear comrads, thanks for helping me.

I am doing nothing to mount my external HD. I am junst plugin and the xubuntu is mounting it for me.

Here is my fstab: 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    defaults        0       0
#Entry for /dev/sda3 :
UUID=4000021c-e7ba-4a86-a658-82eb4b129c10       /       ext4    errors=remount-ro,user_xattr    0       1
#Entry for /dev/sda4 :
UUID=4D7213CC72951DED   /media/BACKUP   ntfs-3g defaults,locale=pt_BR.utf8      0       0
#Entry for /dev/sda5 :
UUID=90FC232CFC230BD2   /media/Windows  ntfs-3g defaults,locale=pt_BR.utf8      0       0
#Entry for /dev/sda2 :
UUID=c03d120e-fcc0-428b-bc3d-a70a7a43aeb7       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto,exec,utf8   0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8        0       0


But I think my external vfat driver is not there..


And when I say ''executable'', is a linux executable file. I run Makefile, get an executable and execute it "./myexe.out".

Thank you a lot!

Tiago Carneiro.

---

### Post by dcstar on 2011-11-06
> **carcarah said:**
> Dear members,

i've been searching for a while about this problem, but with no success.

I was ubuntu 10.04 user, and used to execute executables directly from my fat external disk.

But in ubuntu 11.04 I can't. Even changing settings with chmod and so on.

**The only way I can execute is putting the executable in linux partition**.

Do you know how to solve this problem?

Thank you.

Since FAT is a non-linux filesystem I would say the security model has been improved not to allow such risky things to be done.

---

