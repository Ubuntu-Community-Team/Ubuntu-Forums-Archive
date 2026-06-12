---
title: "Clearing out old stuff."
date: 2012-08-24
forum: General Help
---

### Post by Roasted on 2012-08-24
I thought a 15GB partition for root would be enough, but I'm getting bombarded by messages saying my root partition only has 300MB left. I ran ncdu (awesome terminal based disk usage application) to see what was eating the space. It seems like there's a lot in places like /lib, /usr, /opt, etc.

This got me wondering... is there a way I can clear out old kernels and whatnot? I assume they'd be taking up SOME space. Is that the most likely place to start?

NCDU output:


ncdu 1.8 ~ Use the arrow keys to navigate, press ? for help                                                                                           
--- / ------------------------------------------------------------------------------------------------------------------------------------------------
. 108.5GiB [##########] /home                                                                                                                         
    5.2GiB [          ] /usr
.   1.3GiB [          ] /var
  797.8MiB [          ] /lib
. 667.8MiB [          ] /opt
  640.2MiB [          ] /public
  139.3MiB [          ] /boot
   17.4MiB [          ] /tftpboot.fogbackup
   17.4MiB [          ] /tftpboot
.  16.7MiB [          ] /etc
    9.3MiB [          ] /sbin
    9.1MiB [          ] /bin
    5.3MiB [          ] /media
    3.3MiB [          ] /lib32
.   1.2MiB [          ] /run
.  88.0KiB [          ] /tmp
!  16.0KiB [          ] /lost+found
    8.0KiB [          ] /srv
    8.0KiB [          ] /images
    4.0KiB [          ] /dev
    4.0KiB [          ] /lib64
e   4.0KiB [          ] /webdav
e   4.0KiB [          ] /selinux
!   4.0KiB [          ] /root
e   4.0KiB [          ] /mnt
e   4.0KiB [          ] /cdrom
.   0.0  B [          ] /proc
.   0.0  B [          ] /sys
@   0.0  B [          ]  initrd.img.old
@   0.0  B [          ]  initrd.img
@   0.0  B [          ]  vmlinuz.old
@   0.0  B [          ]  vmlinuz

---

### Post by sepo on 2012-08-24
did you apt-cleaned your system? (I see /var is 1.3Gb, but maybe it's ok :D)
In example > apt-get autoclean 
This command removes .deb files for packages that are no longer  installed on your system.  Depending on your installation habits,  removing these files from */var/cache/apt/archives* may regain a significant amount of diskspace.
(excerpt from [https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands) )

There's also the 
```
apt-get remove linux-image-xxxxxx-generic
```to remove kernel packages, but you have to be SURE of what you're doing

Note: apt-get needs 'sudo' permissions

---

### Post by sepo on 2012-08-24
You can also try to understand what's eating space (i.e. in the /usr folder) with 
```
du /usr | sort -g
```
(du is for disk usage, sort is to sort :-D)

---

### Post by OrangeCrate on 2012-08-24
Old thread, but still very valid advice used by many here on the forums:

> 
HOWTO: Cleaning up all those unnecessary junk files

Hello everyone! So, do you ever get the feeling that your system is being flooded with a bunch of junk files that you can't get rid of? I know I do. Well, I'm going to show you a few ways to get rid of most, if not all, of those annoying junk files...


[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by oldos2er on 2012-08-24
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

