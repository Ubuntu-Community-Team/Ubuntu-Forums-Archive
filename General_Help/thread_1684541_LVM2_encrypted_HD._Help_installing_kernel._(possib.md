---
title: "LVM2 encrypted HD. Help installing kernel. (possible fstab issues)"
date: 2011-02-09
forum: General Help
---

### Post by Arabica Bean on 2011-02-09
Hi all. I am in a serious pickle, and I am currently locked out of my OS. I'm running Maverick, and to make things simple, I wanted to migrate from Kubuntu, to Ubuntu. I opened aptitude, and deselected all installed packages, then installed ubuntu-minimal, ubuntu-standard, and ubuntu-desktop for a clean installation (solving all dependancies). The problem arose however when I rebooted, and I realised that I didn't install a kernel. I have gotten pretty far in remounting it using this guide....

[http://ubuntuforums.org/showthread.php?t=940904](http://ubuntuforums.org/showthread.php?t=940904)

Using a live CD, I performed the following...
```

ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 maverick
Enter passphrase for /dev/sda5: 
ubuntu@ubuntu:~$ sudo apt-get install lvm2
ubuntu@ubuntu:~$ sudo modprobe dm-mod
ubuntu@ubuntu:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "pwnsauce" using metadata type lvm2
ubuntu@ubuntu:~$ sudo vgchange -a y pwnsauce
  2 logical volume(s) in volume group "pwnsauce" now active
ubuntu@ubuntu:~$ sudo lvscan
  ACTIVE            '/dev/pwnsauce/root' [224.21 GiB] inherit
  ACTIVE            '/dev/pwnsauce/swap_1' [8.43 GiB] inherit
ubuntu@ubuntu:~$ sudo mkdir /media/root
ubuntu@ubuntu:~$ sudo mount /dev/pwnsauce/root /media/root/
ubuntu@ubuntu:~$ cd /media/root/
ubuntu@ubuntu:/media/root$ sudo mount --bind /proc/ proc/
ubuntu@ubuntu:/media/root$ sudo mount --bind /dev/ dev/
ubuntu@ubuntu:/media/root$ sudo mount /dev/sda1 boot/
ubuntu@ubuntu:/media/root$ sudo chroot ./

```

Once I chrooted into the directory, I installed the 'linux' package, along with lvm2 and cryptsetup and all worked fine, however, the problem lies with what I believe is the fstab file.  It points to the wrong partition. Here is my fstab.

```
 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pwnsauce-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=b347d9ab-e73d-4fb1-9130-41ac95a23b1f /boot           ext2    defaults        0       2
/dev/mapper/pwnsauce-swap_1 none            swap    sw              0       0

```

When I reboot with the current configuration, it goes straight to imitramfs.  I realise that I have to reconfigure the fstab, but I'm at a loss as to what I need to do. Can anyone help me with this? Reinstallation is not a possibility due to the amount of data on the hd.

Many thanks in advance.

---

### Post by Arabica Bean on 2011-02-09
Okay, I managed to make some progress with my problem, but it's only a temporary fix I believe.

I rebooted, and went to initramfs, as it could not find the partition. Catting the proc/cmdline provides...

BOOT_IMAGE=/vmlinuz-2.6.35-25-generic root=/dev/mapper/pwnsauce-root ro quiet splash

By running the following in initramfs, I am able to boot into my system...

```

cryptsetup luksOpen /dev/sda5 maverick
sudo vgchange -a y pwnsauce

```

I have normal boot, but I know that if I reboot, then I will have to restart the procedure all over again. Any pointers as to what I should be looking for? My guess is both grub and fstab.

---

