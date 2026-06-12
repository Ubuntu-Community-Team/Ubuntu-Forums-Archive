---
title: "100% space usage - /dev/mapper/FlexBack-root"
date: 2010-10-03
forum: General Help
---

### Post by banditti on 2010-10-03
Any idea what is going on here?  That file is only 300k.

root@FlexBack:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/FlexBack-root
                       14G   14G     0 100% /
none                 1001M  172K 1000M   1% /dev
none                 1005M     0 1005M   0% /dev/shm
none                 1005M   56K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sda1             228M   36M  181M  17% /boot
192.168.100.73:/mnt/flexstor/flexvol1/of01_nfs01/
                      2.2T  6.8G  2.2T   1% /mnt/of01
192.168.100.71:/vol/ssb
                      800G  736G   65G  92% /home

---

### Post by srs5694 on 2010-10-03
The /dev/mapper/FlexBack-root is a Linux LVM (or possibly a RAID) device file. This means that you've got Linux installed in an LVM or RAID configuration, and the 14GB you allocated for the Linux root (/) in that setup is insufficient.

If you happen to have it installed, I recommend you use the kvpm or system-config-lvm tools to try to increase the space allocated to the FlexBack-root logical volume. If you don't have either of those packages installed, though, installing them might be difficult, since you don't have room left on the root (/) partition. Perhaps you can find something to delete on there to make room -- maybe temporarily uninstall OpenOffice.org or some other big package.

If you need more help, please post the output of the "sudo lvdisplay" and "sudo pvdisplay" commands, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. The output of "sudo fdisk -l" may also be necessary.

---

