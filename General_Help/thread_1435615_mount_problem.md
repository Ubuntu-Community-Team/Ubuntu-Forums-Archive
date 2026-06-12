---
title: "mount problem"
date: 2010-03-21
forum: General Help
---

### Post by mehdi0016 on 2010-03-21
hi
i'm have a problem with mount/unmount my windows drive(sda1 as ntfs format):
i want to mount and unmount this drive every time i need(not auto) without need to input root password.
how could i do this?
i edit my fstab and add this line to it:
/dev/sda1 /media/WinXP ntfs-3g defaults,locale=en_US.UTF-8 0 0
but it auto-mount WinXP drive and JUST root can unmount it.
by the way i have other file in /etc/fstab.pre-ntfs-config that i don't know what is it!?
thanks.

---

### Post by darolu on 2010-03-21
Add the option "**users**" to let your HD be unmounted by any user and not by the user who mounted it only (in this case root).
For example:
```
/dev/sda1 /media/WinXP ntfs-3g defaults,users,exec,rw,locale=en_US.UTF-8 0 0
```
For a full list of options, read [THIS LINK]("http://linux.die.net/man/8/mount") or type "man mount" in your terminal.

I have no idea about the fstab.pre-ntfs-config file.

---

### Post by mehdi0016 on 2010-03-22
thank, but '**users**' option not work:
> Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root.
??

---

### Post by darolu on 2010-03-22
With the '**users**' option, anyone can unmount the device, with the '**user**' option anyone can mount the device.

This is discouraged, but you can achieve what you want by changing permissions or ownership to ntfs-3g, to see its current permissions open a terminal and do:
```
$ ls -l $(which ntfs-3g)
```
You can change permissions or ownership with the [chmod]("http://linux.die.net/man/1/chmod") and/or [chown]("http://linux.die.net/man/1/chown") commands.

---

