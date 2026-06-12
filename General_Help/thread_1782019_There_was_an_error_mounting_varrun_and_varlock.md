---
title: "There was an error mounting /var/run and /var/lock"
date: 2011-06-14
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-14
not solved the correct way, reloaded using the backup i had the foresight to make
i separated / into 3 partitions (/, /tmp, and /var) and after a lot of work (and hair pulling) i can now boot and login but i am getting these 2 errors during bootup

There was an error mounting /var/run
Press S to skip M for manual recovery

There was an error mounting /var/lock
Press S to skip M for manual recovery

```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                           <mount point>   <type>  <options>                  <dump>  <pass>
proc                                      /proc           proc    nodev,noexec,nosuid        0       0
# / was on /dev/sda1 during installation
UUID=31291866-5557-4805-b357-b504685e2cf7 /               ext4    errors=remount-ro          0       1
# /tmp was on /dev/sdb6 during installation
UUID=b04edde4-d0e1-4d41-88e4-19943fa3d1e0 /tmp            ext4    defaults                   0       2
# /var was on /dev/sdb1 during installation
UUID=816d7750-19ba-4440-9248-007356f4770c /var            ext4    defaults                   0       3
# /home was on /dev/sdb5 during installation
UUID=5153a0b4-bfe4-4a91-82c9-f6cbfd5b2018 /home           ext4    defaults                   0       1
# swap was on /dev/sdb7 during installation
UUID=afad817b-8d0e-4a98-8202-81cb3161b490 none            swap    sw                         0       0

# Virtual Machine Storage
UUID=51b2b46b-891c-490c-b8a6-a878595194b6 /mnt/HardDisks  ext4    defaults                   0       4
# RAM disk
tmpfs /home/chad/Desktop tmpfs size=60M,nr_inodes=10k,mode=777 0 0
tmpfs /home/chad/.mozilla/firefox/main.default/Cache tmpfs size=65M,nr_inodes=10k,mode=777   0       0
#tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
``````
~$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sdb6 /tmp ext4 rw 0 0
/dev/sdb1 /var ext4 rw 0 0
/dev/sdb5 /home ext4 rw 0 0
/dev/sdb8 /mnt/HardDisks ext4 rw 0 0
tmpfs /home/chad/Desktop tmpfs rw,size=60M,nr_inodes=10k,mode=777 0 0
tmpfs /home/chad/.mozilla/firefox/main.default/Cache tmpfs rw,size=65M,nr_inodes=10k,mode=777 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/chad/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=chad 0 0
``````
~$ ls -l /var
total 72
drwxr-xr-x  2 root root   4096 2011-06-14 00:15 backups
drwxr-xr-x 18 root root   4096 2011-04-13 07:10 cache
drwxrwxrwt  2 root root   4096 2010-04-13 16:52 crash
drwxr-xr-x  3 root root   4096 2011-04-21 11:48 games
drwxr-xr-x 71 root root   4096 2011-06-13 22:33 lib
drwxrwsr-x  2 root staff  4096 2010-04-23 06:23 local
**drwxrwxrwt  3 root root   4096 2011-06-14 08:10 lock**
drwxr-xr-x 16 root root   4096 2011-06-14 08:10 log
drwx------  2 root root  16384 2011-06-13 20:23 lost+found
drwxrwsr-x  2 root mail   4096 2011-06-14 08:00 mail
drwxr-xr-x  2 root root   4096 2011-02-11 08:04 opt
**drwxr-xr-x 19 root root   4096 2011-06-14 08:10 run**
drwxr-xr-x  8 root root   4096 2011-04-16 23:09 spool
drwxrwxrwt  2 root root   4096 2011-06-14 08:09 tmp
drwxr-xr-x  6 root root   4096 2011-06-05 10:43 www
```background info (i don't like splitting thing apart like this i think it makes it harder to follow)
part 1: [http://ubuntuforums.org/showthread.php?t=1780616](http://ubuntuforums.org/showthread.php?t=1780616)
part 2: [http://ubuntuforums.org/showthread.php?t=1781716](http://ubuntuforums.org/showthread.php?t=1781716)
part 3: [http://ubuntuforums.org/showthread.php?t=1781734](http://ubuntuforums.org/showthread.php?t=1781734)
i hope this is not considered a duplicate thread

---

### Post by pqwoerituytrueiwoq on 2011-06-14
Would knowing some tree info be useful?
```
chad@linux-desktop:~$ tree /var/lock
/var/lock
`-- apache2

1 directory, 0 files
chad@linux-desktop:~$ tree /var/run
/var/run
|-- acpid.pid
|-- acpid.socket
|-- apache2
|-- apache2.pid
|-- atd.pid
|-- avahi-daemon
|   |-- pid
|   `-- socket
|-- console
|   `-- chad
|-- ConsoleKit
|   `-- database
|-- console-kit-daemon.pid
|-- crond.pid
|-- crond.reboot
|-- cups
|   |-- certs [error opening dir]
|   |-- cupsd.pid
|   |-- cups.sock
|   `-- printcap
|-- dbus
|   |-- pid
|   `-- system_bus_socket
|-- gdm [error opening dir]
|-- gdm.pid
|-- hplip
|-- init.upgraded
|-- motd
|-- network
|   `-- ifstate
|-- network-interface-security
|-- NetworkManager.pid
|-- pm-utils
|   |-- locks
|   `-- pm-powersave
|       `-- storage
|-- pppconfig
|-- rsyslogd.pid
|-- samba
|   |-- connections.tdb
|   |-- gencache.tdb
|   |-- messages.tdb
|   |-- upgrades
|   |   `-- smb.conf
|   |-- winbindd.pid
|   `-- winbindd_privileged [error opening dir]
|-- saned.pid
|-- screen
|-- speech-dispatcher
|-- sshd
|-- sshd.pid
|-- sudo [error opening dir]
|-- synaptic.socket
|-- udev-configure-printer
|   `-- usb-uris
|-- unattended-upgrades.lock
|-- upstart-udev-bridge.pid
`-- utmp

23 directories, 35 files
chad@linux-desktop:~$
```

---

### Post by pqwoerituytrueiwoq on 2011-06-14
i found something important in the log viewer
```
init: ureadahead main process (471) terminated with status 5  
mount: mount point /var/run does not exist 
mountall: mount /var/run [481] terminated with status 32 
mountall: Filesystem could not be mounted: /var/run 
mount: mount point /var/lock does not exist 
mountall: mount /var/lock [482] terminated with status 32 
mountall: Filesystem could not be mounted: /var/lock 
fsck from util-linux-ng 2.17.2 
fsck from util-linux-ng 2.17.2 
fsck from util-linux-ng 2.17.2 
fsck from util-linux-ng 2.17.2 
fsck from util-linux-ng 2.17.2 
System: clean, 242280/983040 files, 1372914/3907803 blocks (check after next mount) 
tmp: clean, 28/131648 files, 25443/526120 blocks 
init: ureadahead-other main process (512) terminated with status 4  
var: clean, 9467/131072 files, 104404/524112 blocks 
Home: clean, 10834/1389888 files, 1049462/5574547 blocks (check in 4 mounts) 
init: ureadahead-other main process (525) terminated with status 4  
Virtual_Machines: clean, 12/655360 files, 2478138/2620595 blocks 
init: ureadahead-other main process (539) terminated with status 4  
Skipping /var/run at user request 
Skipping /var/lock at user request 
 * Starting AppArmor profiles       [160G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 [154G[ OK ] 
 * Setting sensors limits       [160G  [154G[ OK ] 
```

---

### Post by pqwoerituytrueiwoq on 2011-06-14
i reloaded a backup reformatted /var and /tmp
left my /home as is
when i 1st booted this time i used recovery mode 
got the cant mount error
used manual recover
chmoded /tmp to 1777
rebooted
it ran a system check
and i did not get the error after that
lets hope i don't get it again on the net reboot (edit no error on reboot)
the reason i loaded a backup was nvidia went all to hell on me

---

