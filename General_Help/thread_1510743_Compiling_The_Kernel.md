---
title: "Compiling The Kernel"
date: 2010-06-15
forum: General Help
---

### Post by Chocrates on 2010-06-15
I am trying to do some kernel development (working on learning how to write drivers) and i need a compiled kernel to do this.  The way i have been doing it for a class on a virtual machine with 2.6.23.17 was just make'ing it then copying it to boot. We used a .config that was given to us that, among other things, didnt use a initrd.

So for my home box running 2.6.32 and 10.4 i tried this for compiling 2.6.34 and .35 and copying /boot/config-`uname -r` and make menuconfig'ing.   No luck.  So i enabled initramfs support and tried to run update-initramfs, which didnt work.  So i followed a few tutorials on using make-kpkg and installing the kernel image and headers.  This time update-initramfs works but still no luck.
Every single time i get a kernel panic vfs failed to boot on device (0,0) .  I didnt touch grub.cfg, but let grub make it for me with grub-mkconfig, so i dont know what is wrong.  For the class when we were getting this kernel panic the problem was a buggy config file, but we never learned what was wrong with it.
So my question is, does anyone know either what would be causing this vfs error, that isnt an initrd problem, or if im making that wrong.
Or if anyone has a good tutorial on all the .config options if that is the problem

Any help would be greatly appreciated.

---

### Post by iponeverything on 2010-06-16
make your modules

make a backup copy of working a initrd image, decompress it and mount it via loopback. Replace the modules in loop mounted initrd with ones from new kernel kernel tree. Unmount and recompress the initrd image. Put in in the correct location and add it to grub config file to be used with new kernel image. 

it might fix your panic's.

---

### Post by Chocrates on 2010-06-16
I am using the vanilla .34 kernel, no test modules or anything yet. Just trying to get set up.

---

### Post by iponeverything on 2010-06-17
Just a wild guess, but I would assume that cause of your panic is a missing module in the initrd. Mount a working initrd and check -- it is not hard.

ext4 perhaps?

Just for the the sake of fun, try using an unmodified version of of a working initrd.

---

### Post by Chocrates on 2010-06-19
Thanks a bunch! i got it working.

I couldn't figure out how to mount the image, it seems the best way to view the files is by
```
gzip -dc /somepath/initrd.gz | cpio -id 
```
since i borrowed the image from a working distribution i think it had ext4 in it, but to be safe i added ext4 to /etc/initramfs-tools/modules and ran update-initramfs for my working image and made sure it booted.
I then did make and make modules_install, unzipped and cpio'd the initrd to a temporary folder, and added the folder /lib/modules/2.6.34-dev to the new temp folder in lib/modules.

to make the image bootable again run:
```
sudo sh -c 'find . | cpio --quiet --dereference -o -H newc |  gzip -9 > /boot/img'
```

---

### Post by iponeverything on 2010-06-23
just for the sake of someone searching in the future.. to mount a an initrd: 

back up your original initrd first.

```

sudo gunzip somepath/initrd.gz 
sudo mount -o loop somepath/initrd /mnt

```

you can then add you modules or check things. Then fix it back with:

```

sudo umount /mnt
gzip somepath/initrd

```

---

