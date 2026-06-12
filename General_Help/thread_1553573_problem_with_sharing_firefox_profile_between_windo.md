---
title: "problem with sharing firefox profile between windows and ubuntu"
date: 2010-08-15
forum: General Help
---

### Post by Honz@ on 2010-08-15
After installing Ubuntu, it didnt automount my windows partitions on startup. I always had to click them in PLACES to mount them. I also had firefox profile folder same as in windows. So every time i started Ubuntu, i clicked on my windows parititon in PLACES and than firefox. It wasnt ideal but it worked. but i wanted them to automount so i edited fstab to be like this
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sdc1 during installation
UUID=e8ef04a7-6907-4f2b-adb7-230ff0d14d32  /            ext4  errors=remount-ro    0  1  
# /home was on /dev/sdc6 during installation
UUID=d8ae72ad-52be-4e4c-a83a-b8f5356bfe69  /home        ext4  defaults             0  2  
# swap was on /dev/sdc5 during installation
UUID=a05d78b4-76b4-4962-91b4-984f4ad7518a  none         swap  sw                   0  0  
/dev/sda2                                  /windows/d  ntfs  rw,auto,user,umask=000             0  0  
/dev/sdb3                                  /media/sdb3  ntfs  rw,auto,user,umask=000             0  0 
/dev/sda1                                  /windows/c  ntfs  rw,auto,user,umask=000             0  0  
```now i cant start firefox with this profile, it says something like "this profile is in use". any idea why it doesnt work now?

---

### Post by sgage on 2010-08-15
Not sure what your issue is now, but what I have been doing for ages with sharing FF stuff between Windows and Ubuntu is to use the Windows install as "home base", and sym-link *.sqlite from the profile there to the profile in Ubuntu. That gives you most everything you need.

With Thunderbird, I simply config my Ubuntu TB to point to the mail store on Windows. I sym-link the adress book from Windows over to Ubuntu. Works great.

All my mail and browsing is transparently shared. I use OpenOffice on both platforms as well. Sometimes I forget which environment I'm in!

---

### Post by Honz@ on 2010-08-16
the symbolic link worked, thx. I dont know why it didnt work when i pointed there directly but it works now, and thats what matters.

---

