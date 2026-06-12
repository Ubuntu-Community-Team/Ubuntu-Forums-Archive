---
title: "Convert Dual-boot to Full Boot?"
date: 2011-03-18
forum: General Help
---

### Post by UnknownDiety on 2011-03-18
I've currently got a Dual-boot of Windows 7 SP1 and Ubuntu 10.10
,
I'm wanting to wipe off the Windows 7 and keep my Current Ubuntu 10.10 (And ofc add the extra space from the Win7 Partition)
I had Win7 Installed first and I used this Guide__ --> [http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/](http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/)
Below is an image of how my hard drive is partitioned currently.

All the Gray = Win7

All the white = Ubuntu


[IMG]http://i54.tinypic.com/2w6tout.jpg[/IMG]

---

### Post by TeoBigusGeekus on 2011-03-18
Boot up with a live cd, fire up gparted and do your thing.

---

### Post by UnknownDiety on 2011-03-18
> **TeoBigusGeekus said:**
> Boot up with a live cd, fire up gparted and do your thing.

I'm asking how to do it, because I don't even know if in the end I should still have 4 for Ubuntu or not.

---

### Post by SavageWolf on 2011-03-18
Open up Gparted in a live CD, format the Windows Partition as "none" (or delete it, rather), stretch the extended partition to 100%. Then you can stretch Ubuntu to the full size (moving the others to the left if needed).

---

### Post by drs305 on 2011-03-18
There are a lot of configurations you can use. 

If you start deleting logical partitions (your Linux partitions) or changing your Ubuntu / partition, even with the LiveCD, don't forget to turn off swap (highlight the swap partition, Partition, Swapoff) or you won't be able to perform any operations.

No matter how you decide to repartition things, before rebooting I'd recommend you run the following:
```

sudo blkid -c /dev/null  # Check the current, non-cached UUIDs
sudo mount /dev/sd**XY** /mnt  # Mount your new Ubuntu / partition.
sudo grub-install --root-directory=/mnt /dev/sda
gksu gedit /mnt/etc/fstab /mnt/boot/grub/grub.cfg # Compare the fstab UUIDs with blkid results
```
Change the fstab and grub.cfg UUIDs to match the blkid results. In grub.cfg - at least for the first (or default) menuentry.

After rebooting without the LiveCD:
```
sudo update-grub
```

---

