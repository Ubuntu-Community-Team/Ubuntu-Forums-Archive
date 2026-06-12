---
title: "reinstall without losing lvm"
date: 2006-06-06
forum: General Help
---

### Post by erimar77 on 2006-06-06
I have an exisiting Ubuntu setup that has been upgraded since flight 1 or so.  I'd really like to do a clean install of the new 6.06 to get rid of some "learning" I did with this current setup.

My problem is, I have an OS drive.. and two 300gb drives setup in LVM.  How can I reinstall my OS making sure that the two drives in LVM remain untouched.. yet accessible after the reinstall?

```
test@ericpc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/VolGroup00/lvol0  /data    ext3    defaults        0       0
```

```
test@ericpc:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             112G   14G   93G  13% /
varrun               1014M  144K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
udev                 1014M  156K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   19M  995M   2% /lib/modules/2.6.15-23-386/volatile
/dev/mapper/VolGroup00-lvol0
                      551G   40G  483G   8% /data
```

---

### Post by mlind on 2006-06-06
I used 'alternative' install cd, which is old ncurses based installer.

When you advance to partition phase, make your LVM active from menu.
Installer prompts it has found previous LVM volumes and asks if you want to
do something about them, reply Cancel or Back - so you get back to partition table
menu.

Then you must set mount points for LVM volumes. You can additionally choose if partition
inside LVM needs to be formatted. 'Untouched' is the default action.

Also, you must remember to set bootable partition again.

In a nutshell, assign mount points only, but don't choose to format the partitions.

---

