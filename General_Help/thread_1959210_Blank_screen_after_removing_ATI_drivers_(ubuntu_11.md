---
title: "Blank screen after removing ATI drivers (ubuntu 11.10)"
date: 2012-04-15
forum: General Help
---

### Post by darkmediator on 2012-04-15
Hi,
 I'd been following this tute : [http://ubuntutechnical.wordpress.com/2011/11/20/install-ati-official-drivers-in-ubuntu/#comment-108](http://ubuntutechnical.wordpress.com/2011/11/20/install-ati-official-drivers-in-ubuntu/#comment-108)

I followed till it says, "After the reboot all the fglrx packages will be gone, you will be using default ones.".

After rebooting, the grub screen shows up. But it shows blank if I chose any of the options i.e normal boot or boot with recovery mode. 

It just shows a blank screen and I can't complete the further part of the tutorial. Please help.

ATI card : Radeon 6770

---

### Post by darkmediator on 2012-04-17
OK, the problem has been solved...

What I did

1. Boot from Ubuntu Live CD and continue trying Ubuntu 11.10
2. Open terminal and execute
```

sudo mount /dev/sda2 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

```
...where /dev/sda2 is the root partition 
3. Install the ati drivers normally
4. Reboot and Voila...! :)

---

