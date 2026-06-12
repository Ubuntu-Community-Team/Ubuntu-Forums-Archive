---
title: "Setup RAID 1 on running system"
date: 2010-10-22
forum: General Help
---

### Post by Macsloverd on 2010-10-22
Dear all,

This is a problem I've got in Debian Lenny, I usually work with Ubuntu and basically, I have no idea where to find help for Debian, here is the only good place I know.

I followed the instructions from here [http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub-configuration-debian-lenny](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub-configuration-debian-lenny) (it is too long to post it here) to setup a raid 1 system for my lenny server. Instead of 3 partitions I only have two: sda1=/ sda2=swap (in the above mentioned instructions there are three, /, /boot and swap). Every thing seems fine until I worked onto the end of page 2 -> reboot. I could not boot into the system after grub start to load the system: md0 does not exist.

the process in this instructions is basically like this:
1. install the raid tools;
2. make the sdb partition table as the same as the sda;
3. change the partition type of sdb into linux raid auto;
4. create raid arrays and add sdb partitions into it while using missing as place holder for sda partitions since the system is still running on them;
5. create raid file systems on md0, md1;
6. adjust the fstab replace sda's with md's;
7. edit grub menu.list to make the next system start from kernal /dev/md0 (which now only contains sdb1), root in hd1,0;
8. adjust the ramdisk with update-initramfs -u;
9. cp -dpRx / /mnt/md1 to mirror sda1 to sdb1(which now is md1);
10. configure and install (for me it more like re configure and re-install) grub on sda and sdb;
11. quit grub command line and reboot -> here is where I got stuck: md0 does not exist.

I noticed that in step 8 updating the ramdisk instead of displaying vmlinuz-2.6.26-2-686, it showed vmlinuz-2.6.26-2-486 or something like this with 486 in the end for sure. When I edit the menu.list temporarily when booting grub (press e to edit the parameters in the blueish screen) to boot either from sda or sdb, it works, the only thing is that md0 does not exist.

So does anyone have any idea how I am going to solve this problem? This is on a production server so it's kinda important to me, so please....anyone.

Thanks in advance.

---

