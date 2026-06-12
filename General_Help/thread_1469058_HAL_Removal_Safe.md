---
title: "HAL Removal Safe?"
date: 2010-05-01
forum: General Help
---

### Post by sports fan Matt on 2010-05-01
I am wondering if I removed HAL & ureadhead from Lucid via Synaptic, would my machine boot & does it make much of a difference in boot times?

I've heard yes, but would rather ask first then assume and then spend an hour reinstalling everything :)

---

### Post by sports fan Matt on 2010-05-02
Anyone know?

---

### Post by GSF1200S on 2010-05-03
> **sox fan Matt said:**
> Anyone know?

Well, I cant remove it from my install because some of my XFCE apps still require hal (thunar-volman, xfce-power-manager, etc). However, I booted my 10.04 Lucid virtual machine in Sun VirtualBox and removed hal and ureadahead, and it booted fine. It did almost seem faster, but perhaps im just being optimistic. You wouldnt need to reinstall if that broke anything though- just boot a liveCD, chroot into the partition, copy /etc/resolv.conf on the liveCD to /mnt/etc/resolv.conf (assuming /mnt is where you mounted 10.04's partition when setting up the chroot), and reinstall the packages hal and ureadahead. Reboot, back to business.

If youre feeling froggy, you might as well give it a shot. If you need any help with chroot, heres a basic run-through:

Use the command:
```
sudo fdisk -l
```
and find out what partition / is installed on. Then, assuming /dev/sda1 is that partition, you would do the following:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
```

Then, to get those packages, do:
```
sudo apt-get update
sudo apt-get install hal ureadahead
```

Then to unmount the partitions:
```
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /dev/sda1
```

Then reboot into the hard drive install.. should work.

---

### Post by nanog on 2010-05-03
hal is depcrecated for boot but not yet for a good part of gnu/linux. the list of programs that still use hal is in the thousands. 

here is one example that makes hal a complete necessity for me:

$ sudo apt-cache depends virtualbox-3.1 | grep hal
  Recommends: libhal1

without hal usb functionality is completely lost in vbox.

---

### Post by 3rdalbum on 2010-05-03
Removing HAL (assuming it is not needed) will not appreciably improve your bootup time.

---

### Post by nanog on 2010-05-03
"will not appreciably improve your bootup time"
erm...because its no longer used for boot. its all udev now...

---

### Post by sports fan Matt on 2010-05-03
I'm gonna try it. If it fails I can chroot.  We shall see, was just petrified to try it until I had a few opinions:)

---

### Post by sports fan Matt on 2010-05-03
Well, it is gone and the system booted right up.  Maybe I need to stop being so pessimistic when it comes to these sort of things.

---

