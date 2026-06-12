---
title: "Need help move grub2 from sda to sdb"
date: 2010-04-19
forum: General Help
---

### Post by Doctor Mike on 2010-04-19
Need help removing grub2 from sda HDD and placing on sdb where Ubuntu is installed.
Was doing a fresh install of 9.10 after Lucid beta testing and the install cd I used was a little older and didn't provide a choice of where to install the grub.

sda is a XP install and I don't want to have to rely on grub for both systems.

---

### Post by carl4926 on 2010-04-20
sdb need to be set to first in BIOS boot order.
If that changes the mapping of the HD's from when you originally installed. You may need to use the Ub CD
otherwise it should be just as follows:

```
sudo update-grub
```

```
sudo grub-install /dev/sdb
```


Using the CD method:

Open a terminal and type

$ sudo fdisk -l

Now, you need to remember which device listed is your linux distribution, for reference, /dev/sdb1 will be used. Now we need to mount the filesystem to /mnt

$ sudo mount /dev/sdb1 /mnt

Now mount the rest of your devices

$ sudo mount --bind /dev /mnt/dev

Now chroot into your system

$ sudo chroot /mnt

  

When that is done you need to run update-grub to create the configuration file.

$ update-grub

    

To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda

$ grub-install /dev/sdb

And your done

---

### Post by Doctor Mike on 2010-04-20
> **carl4926 said:**
> sdb need to be set to first in BIOS boot order.
If that changes the mapping of the HD's from when you originally installed. You may need to use the Ub CD
otherwise it should be just as follows:

```
sudo update-grub
``````
sudo grub-install /dev/sdb
```
Using the CD method:

Open a terminal and type

$ sudo fdisk -l

Now, you need to remember which device listed is your linux distribution, for reference, /dev/sdb1 will be used. Now we need to mount the filesystem to /mnt

$ sudo mount /dev/sdb1 /mnt

Now mount the rest of your devices

$ sudo mount --bind /dev /mnt/dev

Now chroot into your system

$ sudo chroot /mnt

  

When that is done you need to run update-grub to create the configuration file.

$ update-grub

    

To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda

$ grub-install /dev/sdb

And your doneYes sdb (can) boots first and is still sdb. Will grub2 be removed from sda by this process?

---

### Post by carl4926 on 2010-04-20
No
If you want to fix XP's bootloader
Use the XP CD to fixmbr.

But XP should still boot from grub without doing that.

---

### Post by Doctor Mike on 2010-04-20
> **carl4926 said:**
> No
If you want to fix XP's bootloader
Use the XP CD to fixmbr.

But XP should still boot from grub without doing that.Ya I don't want to rely on grub. Had a similar situation when I went to Lucid beta and got two copies of grub, the one on sda was corrupt and fixmbr and suprgrub couldn't fix it. Had to restore from image. Will loose more data this time if I have to use an image file.

---

### Post by Doctor Mike on 2010-04-20
Thanx Carl. Everything has worked out well...:)

---

### Post by carl4926 on 2010-04-20
> **Doctor Mike said:**
> Thanx Carl. Everything has worked out well...:)
This is good news!

---

