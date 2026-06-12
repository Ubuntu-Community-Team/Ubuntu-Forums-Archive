---
title: "diskutil: command not found AND associated problem"
date: 2011-09-15
forum: General Help
---

### Post by 118118 on 2011-09-15
hi,
 
i'm trying to gain write access to hfs+ formatted external hard drive. running ubuntu 11.4
 
i found this guide [http://somethingkindawierd.com/blog/computers/linux-computers/08/2009/readwrite-to-hfs-on-ubuntu/](http://somethingkindawierd.com/blog/computers/linux-computers/08/2009/readwrite-to-hfs-on-ubuntu/) but it did not work for me.
 
that is, i added the following to the text document at /etc/fstab
 
/dev/sdb3 /mnt/common hfsplus user,auto,uid=1000,gid=1000 0 0

and did not gain write access. 
sdb3 is the path to the current partition that has read access. when i type "mount" i see that this partition has no user id [that is what i assume nosuid means], i don't know if that's relevant.
 
there was a link here [https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus) to the following site [http://en.gentoo-wiki.com/wiki/Hfsplus](http://en.gentoo-wiki.com/wiki/Hfsplus) and it was suggested that i run the command
 
sudo diskutil disableJournal /Volumes/TheVolumeName
 
but when i do i get
diskutil: command not found
 
thanks for any help

---

### Post by foureyesboy on 2011-09-15
That 'diskutil' is the command on Mac OS X in this context.

---

### Post by 118118 on 2011-09-15
oh how silly of me... i've changed the title of the thread :)

---

