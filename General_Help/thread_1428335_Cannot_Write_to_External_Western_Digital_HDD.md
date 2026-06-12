---
title: "Cannot Write to External Western Digital HDD"
date: 2010-03-12
forum: General Help
---

### Post by bobloblaw86 on 2010-03-12
Using Latest and Updated Ubuntu, plugged in my external drive and was able to copy files from it to my linux box, but unable to transfer media to the drive. I tried using nautilus to give permission to user account but it won't allow me to change it. It is fat32 format and is my parents so it has barely been used and never formatted whatsoever. What am I doing wrong? Thanks!

Output of 'mount' 
[FONT=monospace]/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/joo/.Private on /home/joo type ecryptfs (ecryptfs_sig=4b3f6d31717735a7,ecryptfs_fnek_sig=5a99bca76adc917e,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/joo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joo)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=joo)
/dev/sdb1 on /media/ type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


Also I am able to transfer data on to it with a windows machine.
[/FONT]

---

