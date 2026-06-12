---
title: "Boot problems after kernel update"
date: 2012-01-22
forum: General Help
---

### Post by gustavo0 on 2012-01-22
I recently swtiched to Ubuntu from OpenSUSE (dual boot with Windows), and everything was working fine until the update manager updated my kernel from 3.0.0.14-generic to 3.0.0.15-generic. 

Now Ubuntu won't load. After I select the default Ubuntu (latest kernel version) on the grub screen it says 'error: couldn't read file, press any key to continue', and pressing a key does absolutely nothing. 

When I tried to boot it in recovery mode, it gave me the following output

[PHP]
(...)
Cannot open root device "UUID=1bd76c90-ce85-4b7f-9e6d-2427ad2b4791" or unknown block(0,0)
Please append a correct "root=" boot option; here are the available partitions //it lists nothing
Kernel panic - not syncing: YFS: Unable to mount root fs on unknown block (0,0)
(...)
[/PHP]I can load Ubuntu, however, if I choose any older kernel among the 'previous linux versions'.

The boot-repair thing gave me this as a result:
[http://paste.ubuntu.com/813220/](http://paste.ubuntu.com/813220/)

My /etc/fstab looks quite strange: 

[PHP]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=1bd76c90-ce85-4b7f-9e6d-2427ad2b4791 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=b0fa38ad-e251-4045-b04c-a76a0aac8080 none            swap    sw              0       0[/PHP]I would appreciate any kind of help.

---

### Post by gustavo0 on 2012-01-22
I have done the idiot thing - reinstall the latest kernel - and it works. Sorry for wasting your time.

---

