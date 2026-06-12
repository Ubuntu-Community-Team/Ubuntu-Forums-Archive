---
title: "Shutdown hangs on umount process"
date: 2011-11-30
forum: General Help
---

### Post by illuminate1 on 2011-11-30
I am starting to think Ubuntu hates me.. I have spent hours on this and still no clue! Newbie user running Ubuntu 10.04.1 LTS Linux version 2.6.32-24-generic. Some of the errors I am getting when trying to do a shutdown or init 6:

```
* Unmounting local filesystems...                        [OK]
[22920.472053]  INFO: task flush-8:0:1501 blocked for more than 120 seconds.
[22920.494810] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[22920.5175841] INFO: task umount: 1690 blocked for more than 120 seconds.
[22920.528858] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
```My fstab and mtab information:
```

root@server01:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/cciss/c0d0p1 during installation
UUID=bb5471ee-7741-4859-a12c-5dc533ecf57c /               ext4    errors=remount-ro 0       1
# swap was on /dev/cciss/c0d0p5 during installation
UUID=21c07a6f-5d34-44fa-a6b3-f942c31bf528 none            swap    sw              0       0
UUID=f11ab204-d831-4841-abb6-5780d9b485a3 /backups      ext4    defaults       00
UUID=55c51535-8775-495e-91fd-e00c44d5208f /backups2     ext4    defaults       00

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1       /mnt/usb        ext3    user,noauto,rw          0       0
root@server01:~# cat /etc/mtab
/dev/cciss/c0d0p1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/cciss/c0d1p1 /backups ext4 rw 0 0
/dev/sda1 /backups2 ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
```
At one point, I had this server rebooting just fine. I had drive use at 100% after a copy to a mount went wrong and recently cleaned that up. Not sure if that is relevant or not, but it seems to be when this issue began. I have to physically power cycle the server to bring it back up at this point. Any assistance would be most appreciated!

---

### Post by Spyderkid on 2011-11-30
when shutting down you could use the terminal and type ```
sudo Poweroff
``` into it?

It's just a suggestion

---

### Post by illuminate1 on 2011-11-30
Poweroff produces the same results listed above.

---

### Post by illuminate1 on 2011-11-30
Ideas anyone? Things I can try? :confused:

---

### Post by BC59 on 2011-11-30
Check here, if the solution can help you:

[http://ubuntuforums.org/showthread.php?t=1858171](http://ubuntuforums.org/showthread.php?t=1858171)

---

### Post by illuminate1 on 2011-11-30
BC59~ thanks for the link.. I think my issue is  different though, because shutdown and reboot both are hanging.. I will check out the solution further though and try!

---

### Post by illuminate1 on 2011-11-30
looks normal, yes?

```
lrwxrwxrwx   1 root root    23 2010-09-05 12:31 K20openbsd-inetd -> ../init.d/openbsd-inetd
lrwxrwxrwx   1 root root    17 2010-09-05 12:31 K50proftpd -> ../init.d/proftpd
lrwxrwxrwx   1 root root    19 2010-08-31 08:46 K74bluetooth -> ../init.d/bluetooth
-rw-r--r--   1 root root   353 2009-09-07 13:58 README
lrwxrwxrwx   1 root root    29 2010-08-31 08:46 S10unattended-upgrades -> ../init.d/unattended-upgrades
lrwxrwxrwx   1 root root    22 2010-08-31 08:46 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx   1 root root    18 2010-08-31 08:46 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx   1 root root    17 2010-08-31 08:46 S30urandom -> ../init.d/urandom
lrwxrwxrwx   1 root root    22 2010-08-31 08:46 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx   1 root root    20 2010-08-31 08:46 S35networking -> ../init.d/networking
lrwxrwxrwx   1 root root    18 2010-08-31 08:46 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx   1 root root    20 2011-10-05 09:59 S41open-iscsi -> ../init.d/open-iscsi
lrwxrwxrwx   1 root root    20 2010-08-31 08:46 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx   1 root root    14 2010-08-31 08:46 S90halt -> ../init.d/halt
```

---

### Post by illuminate1 on 2011-12-01
Are there any files I can check that might point me in the right direction? I looked in the dmesg and messages logs but I'm not necessarily sure what I am looking for in there.

---

