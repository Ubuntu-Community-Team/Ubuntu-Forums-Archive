---
title: "separate partition /boot and 2 xubuntu installations"
date: 2012-05-25
forum: General Help
---

### Post by linuxcss on 2012-05-25
like to have 2 slightly different installations of  xubuntu on same disk
and have /boot shared by both installations

attempted this:

/dev/sda1  installation #1 all in one partition except for /boot partition
/dev/sda5 /boot  (noswap)

then installation #2 
/dev/sda6 swap
/dev/sda7 /
/dev/sda8 /home
/dev/sda5 /boot (but no reformat)

after finishing the installation #2
when i boot grub menu has both installations available to boot but when selecting the installation #1 ... it always boots the installation #2

what is wrong ? Or what is the proper way to achieve this and still have /boot as separate partition?

---

### Post by ajgreeny on 2012-05-25
Why do you want a separate /boot partition?

If you leave boot in the root of each OS which is what wil happen if you do not specify a separate /boot partition, grub 2 will find both of them when you install the second OS, and both Xubuntu versions will be shown in the grub menu.

---

### Post by oldfred on 2012-05-25
I also do not recommend separate /boot for desktops unless you have an old system with the 137GB BIOS boot limit, or a server type install with LVM or RAID.

If you really want separate /boot you have to have a separate /boot for every system you install. Otherwise you get conflicts in the kernels, vmlinuz, & grub files.

---

### Post by linuxcss on 2012-05-25
thanks for insight oldfred ... I thought it was possible to easily have a  single /boot shared by 2 or more installations

If I want to have a partition with /boot to only select other installations that each have their own boot code, what is a good reference for that?

---

### Post by oldfred on 2012-05-25
You can just have one install with a separate /boot and keep the others inside / (root). Grub2's os-prober will find all the other installs and let you boot them.

You can create a grub only  partition (not /boot), but then os-prober is not there, only grub2's boot files. You then have to manually update grub.cfg for each install. I do that for some of my flash drives as I boot them with grub loopmounts of ISO files directly. You can manually create boot stanzas that only boot the newest kernel, so a lot of updating is not required. But I think that only works with Debian based LInux as they have links in / to the newest kernel that you use.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

