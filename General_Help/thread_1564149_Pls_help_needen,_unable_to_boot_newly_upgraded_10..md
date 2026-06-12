---
title: "Pls help needen, unable to boot newly upgraded 10.04"
date: 2010-08-30
forum: General Help
---

### Post by eriksson25 on 2010-08-30
Hi, I have a server that has been runing since 8.10. But needed to plug in a ext4 disk so thought that why not upgrade to 10.04. Everything went fine up to 9.10 but after last upgrade step to 10.04 I am unable to boot up.

Its a basic setup, one system 160 ide disk (ext3). One lvm system containing 4 disks. And then a mdadm raid 5 array with 4 disks.

My motherboard is a Asus P5B delux, it has a jmicron sata/ide controler 

In grub I get several kernel options.

The latest 2.6.32-24 Gives be a complete green screen that is frozen. Nothing more. Same kernel in recovery mode continues but then the screen just go black and nothing hapends.

Kernel 2.6.28-19 gives me /scripts/init-top/brltty: 20:grep:not found. Error: unexpectedly disconnected from boot status daemon.
Then stands ticking on my mdadm raid 5 aray. Then foliwing error gave up waiting for root device. Alert /dev/disk/by-uuid xxxx-xxx-xxx does not exist. dropping to shell. 
initramfs

Kernel 2.6.27-17 recovery mode I see it listing my sdj that is my system disk. / is on sdj1 and swap on sdj2. But it gets stuck un "begin: waitning for root file system" then gives the same error as last kernel.

Kernel 2.6.24-22 and lower gives me folowing error.
```
init:unreadahead main process (3283) terminated with status 5. libudev: udev_monitor_new_fromnetlink: error getting socket: invalid argument mountall:mountall.c:3204: Assertion failed in main: udev_monitor = udev_monitor_net_from_netlink (udet, "udev")
init: mountall main process (3286) killed by abrt signat. General error mounting filesystems
``` and then drops me to a maintenace shell where I can mount and change in my root system no problem.

So I realy need help, have been strugeling with this 20h+ and googeling everything I could think of.

---

### Post by eriksson25 on 2010-08-30
Oki, Some more information. After several houres I got it to boot but it still not fixed. What I did was unplug all other disks other then system disk. This way it is named /dev/sda no mather how many times I reboot. Then I went thrue maintenece shell and changed /etc/fstab to mount /dev/sda1 as root and sda2 as swap. I then went to /boot/grub/menu.lst and changed it to boot root /dev/sda1 Then it booted and everything worked. But here comes the big BUT

If I plug in my disks again then it all breaks down, /dev/xxx changes for every reboot most of the time its sdj but also sdi, sdh and so on. If I change it to UUID it dosent work, it gives the same error as last time waiting for root. So I cant use UUID

So I need help how to get the system disk to stay sda even when I plug in other disks.

I have tried label the partitions but dont thing grub works with that, it gave me same error anyway.

---

