---
title: "Sudden non boot and restore grub prompt! Help!"
date: 2010-01-24
forum: General Help
---

### Post by proficio on 2010-01-24
I've got Linux Mint Helena running on a Toshiba Laptop.  Its worked flawlessly for months now and I love it(long time windows slave).  Earlier today I was attempting to do some sort of disk error checking on my wifes blackberry sd card.  Having never done this before with linux I did some searching and ended up ignorantly running a couple of terminal commands.  I was tired and really don't even remember what I ran.  Something like fdchk or chsk.  Anyways after a couple of minutes I noticed the computer slowing and then programs would not load.  Tried to reboot but it did nothing.  I cut power and restarted then received an invalid filesystem error and restore grub prompt.............I've booted from the live cd and attempted to mount the partition as a starting point using the following command:

sudo mount /dev/sda1 /mount

When I do this it gives an error message saying must specify file system type.  I have used the fdisk -l command and verified the mount command is right. I can view the drive in disk checker and it appears healthy.

Im at a loss. Any help would be greatly appreciated!!!

---

### Post by 73ckn797 on 2010-01-24
What version of Ubuntu are you using?

---

### Post by proficio on 2010-01-24
> **73ckn797 said:**
> What version of Ubuntu are you using?

Im using Linux Mint Helena which Im fairly certain is just a fancy Ubuntu 9.10.

---

### Post by 73ckn797 on 2010-01-24
> **proficio said:**
> Im using Linux Mint Helena which Im fairly certain is just a fancy Ubuntu 9.10.
OPPS!! you did state that.

Try running:
```
sudo grub-update
``` in terminal.

---

### Post by proficio on 2010-01-24
It says command not found!

---

### Post by Jackzor on 2010-01-24
> **proficio said:**
> It says command not found!

```
sudo update-grub
```

---

### Post by 73ckn797 on 2010-01-24
> **Jackzor said:**
> ```
sudo update-grub
```


OPPS! I am not focused tonight. I will shut this computer down.

---

### Post by proficio on 2010-01-24
LOL

I tried it and got this.

> mint@mint ~ $ sudo update-grub
grub-probe: error: cannot find a device for /.



---

### Post by proficio on 2010-01-24
Tried this too:

> mint@mint ~ $ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6cdffdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris
mint@mint ~ $ sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type
mint@mint ~ $ 


---

