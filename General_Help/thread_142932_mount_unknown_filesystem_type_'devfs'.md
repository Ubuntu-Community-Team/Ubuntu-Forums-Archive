---
title: "mount: unknown filesystem type: 'devfs'"
date: 2006-03-11
forum: General Help
---

### Post by sYs^ on 2006-03-11
Hi!

Today I installed  Kubuntu 5.10, first everything was alright but after i updated my kernel to 2.6.15.6 (i used the default config, which is installed by kubuntu) i could read only that hdd which has kubuntu installed, i have two other hdds with ntfs and they were working fine before updating my kernel, but now when i try to mount them at System Settings -> Disk & Filesystems, it writes:

Return code from mount was 32.
"mount failure"

At booting it writes: mount: unknown filesystem type: 'devfs'

My fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hdc3 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hdc6 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0
/dev/hdc5 /home/dani/g ntfs ,uid=1000,gid=1000,auto,rw,owner 0 0
/dev/hdb1 /home/dani/f ntfs ,uid=1000,gid=1000,noauto,rw,owner 0 0
/dev/hda1 /home/dani/d ntfs ,uid=1000,gid=1000,noauto,rw,nouser 0 0

I read that devfs is removed from that kernel version which i am using, so perhaps that's the problem, but i don't know how to replace it with anything.

Sorry, but i am totally noob @ kubuntu :\
Thanks for your answers.

Regards sYs^

---

