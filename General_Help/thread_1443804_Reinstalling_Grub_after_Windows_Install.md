---
title: "Reinstalling Grub after Windows Install"
date: 2010-03-31
forum: General Help
---

### Post by ashkev on 2010-03-31
Hello, I am running 9.10, upgraded from 9.04, si I have GRUB legacy.  I have been trying to follow the instructions from [this page, ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), but I am having difficulty.  I have booted from a 9.04 live cd and mounted the linux partition.  When I type mount | tail -l this is the output:

```
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
```

The page then says "To make sure this is indeed the Ubuntu boot partition, run ls /media/0d104aff-ec8c-44c8-b811-92b993823444/boot, substituting 0d104aff-ec8c-44c8-b811-92b993823444 with your volume's UUID from before, which should output something like this: ```
config-2.6.18-3-686      initrd.img-2.6.18-3-686.bak  System.map-2.6.18-3-686
grub                     lost+found                   vmlinuz-2.6.18-3-686
initrd.img-2.6.18-3-686  memtest86+.bin"
```

My output looks like this: 

```
abi-2.6.28-16-generic         memtest86+.bin
abi-2.6.31-14-generic         System.map-2.6.28-16-generic
abi-2.6.31-15-generic         System.map-2.6.31-14-generic
abi-2.6.31-16-generic         System.map-2.6.31-15-generic
abi-2.6.31-17-generic         System.map-2.6.31-16-generic
abi-2.6.31-19-generic         System.map-2.6.31-17-generic
abi-2.6.31-20-generic         System.map-2.6.31-19-generic
config-2.6.28-16-generic      System.map-2.6.31-20-generic
config-2.6.31-14-generic      vmcoreinfo-2.6.28-16-generic
config-2.6.31-15-generic      vmcoreinfo-2.6.31-14-generic
config-2.6.31-16-generic      vmcoreinfo-2.6.31-15-generic
config-2.6.31-17-generic      vmcoreinfo-2.6.31-16-generic
config-2.6.31-19-generic      vmcoreinfo-2.6.31-17-generic
config-2.6.31-20-generic      vmcoreinfo-2.6.31-19-generic
grub                          vmcoreinfo-2.6.31-20-generic
initrd.img-2.6.28-16-generic  vmlinuz-2.6.28-16-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-15-generic  vmlinuz-2.6.31-15-generic
initrd.img-2.6.31-16-generic  vmlinuz-2.6.31-16-generic
initrd.img-2.6.31-17-generic  vmlinuz-2.6.31-17-generic
initrd.img-2.6.31-19-generic  vmlinuz-2.6.31-19-generic
initrd.img-2.6.31-20-generic  vmlinuz-2.6.31-20-generic

```

I know that this is the linux partition, but I am afraid to go further as this output looks so different from the example.  

Should I keep going and type ```
sudo grub-install --root-directory=/media/disk /dev/sda
```?

Thanks,

Kevin

---

### Post by burton247 on 2010-03-31
When in the liveCD what happens if you try:

```

Sudo grub
find /boot/grub/stage1
root(hdx,y)
setup(hdx)
quit

```

find /boot/grub/stage1 will tell you where grub is ( (hdx,y) )

---

### Post by ashkev on 2010-03-31
Thanks for the reply.  I just went ahead and followed the rest of the instructions, and Grub was installed.  When I booted Windows was not there, but I added an entry to /boot/grub/menu.lst and now everything is working fine.

Thanks,

Kevin

---

### Post by burton247 on 2010-03-31
Ok cool. Yeah if you install grub this way it often wont add the windows partiton (not sure if the same goes for other OS's)

---

