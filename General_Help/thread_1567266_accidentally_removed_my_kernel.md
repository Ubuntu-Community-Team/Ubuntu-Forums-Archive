---
title: "accidentally removed my kernel"
date: 2010-09-03
forum: General Help
---

### Post by obirama on 2010-09-03
hi guys,

I use ubuntu for months but it's my first time here, so please be gentle on me :). today i just did some maintenance and cleanup on on my Ubuntu lucid.Found several package of kernel that not been used so i've decided to remove them.unfortunately i also removed kernel that running my ubuntu(2.6.32-19-generic).now whenever i boot into ubuntu, grub just give me 'file not found' and 'load your kernel first' error. i tried solution in [http://ubuntuforums.org/showthread.php?t=1543930]("http://ubuntuforums.org/showthread.php?t=1543930") but not succeed.i am running dual boot lucid and vista(lucid installation using wubi).
when i run these command in my LiveCd terminal :
```
sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys  && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```
it just give me
```
mount: mount point /mnt/dev does not exist
```

is there any difference between native install and wubi installation?
Hope u guys can help me.Clean install of my ubuntu would be my last resort since i done a lot of customization and some important file left in there.thanks

---

### Post by bcbc on 2010-09-03
> **obirama said:**
> hi guys,

I use ubuntu for months but it's my first time here, so please be gentle on me :). today i just did some maintenance and cleanup on on my Ubuntu lucid.Found several package of kernel that not been used so i've decided to remove them.unfortunately i also removed kernel that running my ubuntu(2.6.32-19-generic).now whenever i boot into ubuntu, grub just give me 'file not found' and 'load your kernel first' error. i tried solution in [http://ubuntuforums.org/showthread.php?t=1543930]("http://ubuntuforums.org/showthread.php?t=1543930") but not succeed.i am running dual boot lucid and vista(lucid installation using wubi).
when i run these command in my LiveCd terminal :
```
sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys  && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```
it just give me
```
mount: mount point /mnt/dev does not exist
```

is there any difference between native install and wubi installation?
Hope u guys can help me.Clean install of my ubuntu would be my last resort since i done a lot of customization and some important file left in there.thanks

So you boot a live CD, you mounted your windows partition, and then you loop mounted your wubi root.disk. 

Now you're trying to chroot into it?

Or did you miss a step?

EDIT: ok I can see now you missed the loop mount.

So if windows is on /dev/sda3, then mount it:
```
sudo mkdir -p /media/win && sudo mount /dev/sda3 /media/win
```

```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```

The last command replaces the "sudo mount /dev/sda3 /mnt" from the command you listed.

---

### Post by Rasa1111 on 2010-09-03
bcbc~ that is some pro awesomeness! lol :D
Niice! <3

---

### Post by obirama on 2010-09-04
@bcbc thanks for the quick reply

before i go further i must tell that i install wubi in D:(labelled DATA) partition.anyway,using your method i think could get into chroot environment.
but when i tried to install my kernel it cant be found
```
root@ubuntu:/home/ubuntu# apt-get install linux-image-2.6.32-19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.32-19-generic
root@ubuntu:/home/ubuntu# apt-get install linux-header-2.6.32-19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-header-2.6.32-19-generic
```i tried synaptic
```
root@ubuntu:/# gksu synaptic
No protocol specified

(gksu:3385): Gtk-WARNING **: cannot open display: :0.0
```i did try "sudo update-grub" though
```
root@ubuntu:/# sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-25-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/vmlinuz-2.6.32-23-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```so i'm assuming my ubuntu still have other kernel installed but not my running kernel.is there any way to use these kernel instead of installing running kernel(2.6.32-19)
But i dont mind to install any kernel as long as i can get back to my ubuntu.thanks

p/s:
funny thing, i even can ran apt-get update and apt-get upgrade but not install my kernel.

---

### Post by Silent Warrior on 2010-09-04
o_O I've removed the running kernel before, and never had THAT happen to me...
I actually think those kernels grub detects will be enough to get you into X, at least. But that fstab-alert isn't a good thing. What does cat /etc/fstab tell you? (I didn't need to sudo this. Just in case...)

---

### Post by obirama on 2010-09-04
well it show some error
```
root@ubuntu:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```

---

### Post by bcbc on 2010-09-04
> **obirama said:**
> well it show some error
```
root@ubuntu:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```
I don't see any error in fstab.

I just looked in synaptic and I don't see a linux-image-2.6.32-19-generic package. In the link you referred to, the OP "fh37" was installing the linux-image package.

So give that a try.

EDIT: Also before you exit chroot, run "update-grub" so you get the new kernel in your grub menu. Do not run "grub-install" as you have a wubi install.

PS: in one of your comments you mention that you still have other kernels. Why can't you just use these to boot into wubi? It's easier to do that and reinstall the current kernel than requiring chroot?

---

### Post by obirama on 2010-09-19
hi guys,

sorry for not replying for along time.wifi in my college got some problem.anyway using bcbc suggestion i try to configure grub and it WORKED!!!!!!.i also finally could use vmplayer in my ubuntu(which is the root problem that made me removed my kernel).Frankly i didnt regret to have this problem since i know more about configuring my ubuntu.Million thanks guys :D

---

### Post by yetiman64 on 2010-09-19
Hi Obirama, good to hear all is working, could you mark this thread as solved please if so. Check out link #5 in my sig if you need assistance to do so. yetiman64

---

