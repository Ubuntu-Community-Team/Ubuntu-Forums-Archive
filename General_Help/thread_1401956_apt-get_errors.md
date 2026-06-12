---
title: "apt-get errors"
date: 2010-02-08
forum: General Help
---

### Post by Bender59 on 2010-02-08
Whenever I try to install something, whether it be through apt-get, aptitude, update manager or whatever, I get this error:

error: cannot open `/dev/sdb' while attempting to get disk size

The errors are encountered while installing:

linux-image-2.6.31-19-generic
linux-image-2.6.31-14-generic
linux-image-2.6.31-17-generic
linux-image-generic
linux-generic

Attempting to mount /dev/sdb shows this:

mount: /dev/sdb: unknown device

Does anyone know how I can fix this issue?

---

### Post by Bender59 on 2010-02-08
bump

---

### Post by nothingspecial on 2010-02-08
> **Bender59 said:**
> 


Does anyone know how I can fix this issue?

Not me, but I think it would be prudent to post the output of your partition table.

Type ```
sudo fdisk -l 
``` and post the output here.

It maybe of no use but that is where I would start.

---

### Post by Bender59 on 2010-02-08
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ead7f7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1280    10281568+   7  HPFS/NTFS
/dev/sda2   *        1307       25353   193157527+   7  HPFS/NTFS
/dev/sda3           41360       60801   156167865    5  Extended
/dev/sda4           25354       41359   128568195   83  Linux
/dev/sda5           41360       60053   150159523+  83  Linux
/dev/sda6           60054       60801     6008278+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by nothingspecial on 2010-02-08
I`ll disclaim this right now. I have no idea what`s wrong.

Do you know what /dev/sdb could be.

Did you have another hard drive attatched to ubuntu when you first installed.

See, all your partition table shows is sda and ubuntu, for some reason, is looking for sdb.....what is that?

These are only (very very slightly) more informed guesses than yours.

---

### Post by warp99 on 2010-02-08
Did the kernel updates install anyway?  It may be just benign error.

---

### Post by Bender59 on 2010-02-08
When I try to install, it tells me to restart. After that, it tells me to install it again. Any specific things it would change that I could look for to check if it's being installed?

---

### Post by warp99 on 2010-02-08
Well it looks like it's trying to install the kernal updates to /dev/sdb which doesn't exist according to fdisk. Please run the following commands:

```
:~$ uname -r 

:~$ cat /boot/grub/device.map
```

and post the output to this thread.

---

### Post by Bender59 on 2010-02-08
```
$ uname -r
2.6.31-17-generic
$ cat /boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb
```

---

### Post by warp99 on 2010-02-08
Since you don't have a /dev/sdb drive try this:

Edit your device.map file:
```
sudo gedit /boot/grub/device.map
```
and remove the line "(hd1) /dev/sdb" then save the file:

Run the following command:
```
sudo update-initramfs -u
```

Reboot the computer and try to install the update again.

---

### Post by Bender59 on 2010-02-08
It's not saying anything about /dev/sdb missing, but now I get this:
```
Setting up linux-image-2.6.31-14-generic (2.6.31-14.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.31-14.48 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.31-14.48 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
grub-probe: error: Cannot stat `/usr/share/images/grub'
No path or device is specified.
Try ``grub-probe --help'' for more information.
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.31-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-2.6.31-17-generic (2.6.31-17.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.31-17.54 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.31-17.54 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
grub-probe: error: Cannot stat `/usr/share/images/grub'
No path or device is specified.
Try ``grub-probe --help'' for more information.
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.31-17-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-2.6.31-19-generic (2.6.31-19.56) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
grub-probe: error: Cannot stat `/usr/share/images/grub'
No path or device is specified.
Try ``grub-probe --help'' for more information.
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.31-19-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-19-generic; however:
  Package linux-image-2.6.31-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.19.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 linux-image-2.6.31-14-generic
 linux-image-2.6.31-17-generic
 linux-image-2.6.31-19-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by warp99 on 2010-02-08
Run "sudo update-grub" instead, then reboot.

---

### Post by Bender59 on 2010-02-08
$ sudo update-grub
Generating grub.cfg ...
grub-probe: error: Cannot stat `/usr/share/images/grub'
No path or device is specified.
Try ``grub-probe --help'' for more information.

---

### Post by warp99 on 2010-02-08
For some reason grub is still seeing the /dev/sdb parition as active, but it doesn't exist. Best thing is to reinstall grub using a LiveCD following these directions:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Substitute /dev/sda4 since that appears to be your boot partition unless it's on /dev/sda5.

---

