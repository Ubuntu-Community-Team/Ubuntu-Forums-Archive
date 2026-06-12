---
title: "Boot goes to initramfs shell"
date: 2011-12-16
forum: General Help
---

### Post by isisgrimalkin on 2011-12-16
Hello,

Yesterday my partner decided to unplug an USB hard drive which had a mounted TrueCrypt container, without unmounting either the container or the drive first. This caused the screen to freeze, and a hard reboot was necessary. Now the computer is booting into a Busybox shell (initramfs).

I would like to either make this initramfs problem go away and have my old system back, or at the very least be able to chroot into it and retrieve the files which were not backed up. Please help! 

I searched for this problem and tried booting from a Live USB and doing "sudo fsck /dev/sda" but this came up with no errors and went straight back to the initramfs shell upon reboot. I should also mention that I installed Kubuntu with the alternate install CD, and my hard drive is full-disk encrypted with Luks.

So then I tried chrooting into the filesystem on the hard drive from a Live USB by doing:

1) sudo apt-get install lvm2 cryptsetup
2) sudo modprobe dm-crypt
3) sudo cryptsetup luksOpen /dev/sda5 crypt1
4) sudo vgscan --mknodes
5) sudo vgchange -ay
6) sudo mkdir /media/crypt_root
7) sudo mount /dev/<vg1 name>/root /media/crypt_root

at which point I get the error: 
```
mount: wrong fs type, bad option, bad superblock on /dev/mapper/wintermute-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

and "dmesg | tail" gives:
```
[ 6130.664628] EXT4-fs (dm-1): ext4_check_descriptors: Block bitmap for group 0 not in group (block 3891833065)!
[ 6130.664639] EXT4-fs (dm-1): group descriptors corrupted!

```

---

### Post by isisgrimalkin on 2011-12-16
Alright, so I managed to fix it from the point described in the first post by doing: ```
sudo e2fsck /dev/mapper/vg-root 
``` which had an extremely frightening and long output.  Then, upon reboot, I went into grub, pressed "e" and added the "fastboot" option on the kernel line. The system booted up just fine, but I don't trust that it will continue to do so, so I am making full backups and looking for further information on how to fix the problem. I will report back if I discover anything useful.

---

### Post by isisgrimalkin on 2011-12-16
Alright, so I managed to fix it from the point described in the first post by doing: ```
sudo e2fsck /dev/mapper/-root 
``` which had an extremely frightening and long output.  Then, upon reboot, I went into grub, pressed "e" and added the "fastboot" option on the kernel line. The system booted up just fine, but I don't trust that it will continue to do so, so I am making full backups and looking for further information on how to fix the problem. I will report back if I discover anything useful.

---

