---
title: "Error in available disk space with df command"
date: 2011-03-19
forum: General Help
---

### Post by tokiso on 2011-03-19
Hello,

When I run the 'df' command I get the following result:


/dev/sda1             96120588   4602836  86635016   6% /
none                   3051968       348   3051620   1% /dev
none                   3058820      8872   3049948   1% /dev/shm
none                   3058820       392   3058428   1% /var/run
none                   3058820         0   3058820   0% /var/lock
/dev/sdc1            244196000  21196176 222999824   9% /p2p
/dev/sdb1            358410116 115505340 242904776  33% /datos
/dev/sdb2            1106728020 555753480 550974540  51% /multimedia
/dev/sda2            240309768  11942404 216160312   6% /home
/dev/sda4            138520600  15018868 116465268  12% /windows

The information for the root partition shows that the sum of available and used disk space is lower than total space. Anybody knows what is the reason? Maybe the disk is fragmented.

I am using Ubuntu 10.10 64 bits.

Thanks,

Alvaro

---

### Post by vdobriakov on 2011-07-26
On ext2/ext3 file systems some percentage of space is reserved for operating system needs so it can continue operating even if the disk is (almost) full.

Default setting is 5%. You can change it with tune2fs. I set it to 3% with

    sudo tune2fs -m 3 /dev/sda1

Follow [this link]("http://www.mobile-web-consulting.de/post/8082450139/get-more-free-disk-space-on-ubuntu") to read about more ways to gain space.

---

