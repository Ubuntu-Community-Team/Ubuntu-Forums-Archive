---
title: "Root directory access from LiveCD"
date: 2011-12-19
forum: General Help
---

### Post by gramsyn on 2011-12-19
Can anyone help please?

Can I have access to the root directory of a previously installed Ubuntu version? Something happened and I can get no access to the Grub. I prefer to save some files from Desktop and theen format the whole disk. However from LiveCD access to the root dir is denied.

Thanks

---

### Post by MartijnNL on 2011-12-19
I'm running a Live CD on another pc and I can access the filesystem on the harddisk fine. I just can't access the /root directory, but that's not where files are stored normally (the /root directory is not the same as the root of the filesystem).

But if you really need to access the /root directory press Alt+F2 and run

```
gksu nautilus
```

By the way, you may get access to GRUB back by reinstalling it to the harddisk from the Live CD.

Open a terminal and run:

```
sudo fdisk -l
```

Find the device name for your harddisk (like /dev/sd* , where * is a single letter, /dev/sda for example)

Then run:

```
sudo grub-install /dev/sd*
``` (replace the * with the letter from the device name you just determined. For example:

```
sudo grub-install /dev/sda
```

This might give you your GRUB back.

---

### Post by gramsyn on 2011-12-19
Thanks for the reply,

I tried to install Grub, but terminal returns the following:

```
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?)
```

I think I have to mount the ext partition. How can I do that?

---

### Post by MartijnNL on 2011-12-19
Hmm, you could try using 'Super Grub2 Disk' instead:
[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

That should let you boot into your system. You can then run the 'sudo grub-install /dev/sda' command once you're in your system.

---

