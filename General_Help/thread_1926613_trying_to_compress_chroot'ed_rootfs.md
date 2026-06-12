---
title: "trying to compress chroot'ed rootfs"
date: 2012-02-16
forum: General Help
---

### Post by u-noob-tu on 2012-02-16
Im working on porting Ubuntu to my HP Touchpad by using rootstock and then chroot'ing into it to install a minimal Xubuntu desktop. one of the steps required is giving me trouble. in order to get the rootfs to the Touchpad, i need to compress it. but every time i do so, a file under /proc called kcore stops it dead in its tracks because its over a gigabyte. after a lot of googling, i found out that kcore isnt really a file but more of a process, and there is no way to delete it. is there a way to (im not sure if this is the right term for what im thinking of) "dump" the process? like clearing a cache? or do i just have to wait while the rootfs compresses?

---

### Post by Khayyam on 2012-02-16
> **u-noob-tu said:**
> Im working on porting Ubuntu to my HP Touchpad by using rootstock and then chroot'ing into it to install a minimal Xubuntu desktop. one of the steps required is giving me trouble. in order to get the rootfs to the Touchpad, i need to compress it. but every time i do so, a file under /proc called kcore stops it dead in its tracks because its over a gigabyte. after a lot of googling, i found out that kcore isnt really a file but more of a process, and there is no way to delete it. is there a way to (im not sure if this is the right term for what im thinking of) "dump" the process? like clearing a cache? or do i just have to wait while the rootfs compresses?

u-noob-tu ...

The files in /proc (and also /dev if the system uses udev) are populated at boot, so in your chroot you should just have an empty directory. Your can, if needed, 'mount -o bind /proc /path/to/chroot/proc' and/or 'mount -o bind /dev /path/to/chroot/dev. This will make the chroot 'seem' to be a booted system, and provide the installer with any of resources it might need, but they should be empty dirs where you come to compressing it. 

So, build the system in your chroot, then umount your binds, compress. I'm not sure why you ended up with a /proc/kcore inside your chroot, so I'm not exactly sure how your going about this, but your chroot is just a directory structure mounted onto whatever your Touchpad is booted. I'm not familiar with rootstock so I'm not sure how it works, but I know from hundreds of chrooted installs that its a fairly uncomplicated process.

HTH ... khay

---

### Post by u-noob-tu on 2012-02-16
> **Khayyam said:**
> u-noob-tu ...

The files in /proc (and also /dev if the system uses udev) are populated at boot, so in your chroot you should just have an empty directory. Your can, if needed, 'mount -o bind /proc /path/to/chroot/proc' and/or 'mount -o bind /dev /path/to/chroot/dev. This will make the chroot 'seem' to be a booted system, and provide the installer with any of resources it might need, but they should be empty dirs where you come to compressing it. 

So, build the system in your chroot, then umount your binds, compress. I'm not sure why you ended up with a /proc/kcore inside your chroot, so I'm not exactly sure how your going about this, but your chroot is just a directory structure mounted onto whatever your Touchpad is booted. I'm not familiar with rootstock so I'm not sure how it works, but I know from hundreds of chrooted installs that its a fairly uncomplicated process.

HTH ... khay
thanks for the reply, that clears things up a lot. im starting a new rootstock right now (rootstock basically builds a skeleton root file system that you can chroot into and do whatever you like), and ill try your suggestions. i think i may know how kcore ended up in the chroot. according to the instructions ive been following, after the rootstock is made (when you run rootstock it puts the new root file system in a .tgz) you should uncompress it and then run "mount -t proc proc proc" before chrooting. if im not mistaken, that command ties the rootstock /proc to your system /proc and in effect, mirrors the /proc on the host computer. and therein lies the problem: you then get kcore when you really shouldnt. ill have to put up a revised instruction set for the rootstock/chroot process. all my builds thus far have refused to boot, and this is probably why.

---

