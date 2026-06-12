---
title: "I think i need to reinstall legacy grub (added ssd)"
date: 2011-06-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-13
for the record grub 2 hates my computers that said

i am using legacy grub and already did this
```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0,0)
setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$
```
i changed sda to sdb and made my new ssd sda
copied my boot partition to it
new fstab (with updated comments to make it look original)
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=31291866-5557-4805-b357-b504685e2cf7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=5153a0b4-bfe4-4a91-82c9-f6cbfd5b2018 /home           ext4    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=afad817b-8d0e-4a98-8202-81cb3161b490 none            swap    sw              0       0
# /var was on /dev/sdb1 during installation
UUID=816d7750-19ba-4440-9248-007356f4770c /var            ext4    defaults        0       2
# /tmp was on /dev/sdb6 during installation
UUID=b04edde4-d0e1-4d41-88e4-19943fa3d1e0 /tmp            ext4    defaults        0       2
# ram disk
tmpfs /home/chad/Desktop tmpfs size=60M,nr_inodes=10k,mode=777 0 0
tmpfs /home/chad/.mozilla/firefox/main.default/Cache tmpfs size=65M,nr_inodes=10k,mode=777 0 0
```
old fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=31291866-5557-4805-b357-b504685e2cf7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=5153a0b4-bfe4-4a91-82c9-f6cbfd5b2018 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=6b36b3b7-731a-4372-be35-9f25016f58b9 none            swap    sw              0       0
# ram disk
tmpfs /home/chad/Desktop tmpfs size=60M,nr_inodes=10k,mode=777 0 0
tmpfs /home/chad/.mozilla/firefox/main.default/Cache tmpfs size=65M,nr_inodes=10k,mode=777 0 0
```

---

### Post by pqwoerituytrueiwoq on 2011-06-13
opps *[FONT=Courier New]setup (hd0)[/FONT]* not *[FONT=Courier New]setup (hd0,0)[/FONT]*

---

