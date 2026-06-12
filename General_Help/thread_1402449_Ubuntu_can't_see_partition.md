---
title: "Ubuntu can't see partition"
date: 2010-02-09
forum: General Help
---

### Post by viodelin on 2010-02-09
Yesterday Ubuntu stopped seeing my main data (NTFS) partition. When it first happened I switched to Windows to check it out that way. Windows did some disk checking or similar and then it worked. However, Ubuntu (Heron) still doesn't see the drive. 
Any pointers will be gratefully received.

---

### Post by rocket16 on 2010-02-09
Do one thing, switch to Windows, and backup all your data to any other drive. Now, reformat the partition. And, copy back all the data. Then, it may succeed.

---

### Post by viodelin on 2010-02-09
Thanks for your reply. I have backed up the drive, but reformatting it altogether seems a bit too drastic at this stage. While in windows I found two unopenable files called hal.something and hal.something.lock. I deleted them (probably silly, but they must be still in the recycling bin in windows).
I've rebooted ubuntu and the partition is there now, but it still won't mount. the error message is:

"Unprivileged user cannot mount NTFS block devices using the external FUSE library. Either mount volume as root, or rebuild NTFS-3g with integrated FUSE support and make it setuid root."

So it is a matter of authorisations, but how come, suddenly, and how can I fix it?

Any more help will be greatly appreciated, but I need to go to work now and won't see it till much later.

Thanks again,

---

### Post by john newbuntu on 2010-02-09
Try unistalling "ntfs-3g" from synaptic (system->admin->synaptic package manager) and reinstalling it.  If that does not help, post the output of "cat /etc/fstab" from a terminal and "sudo blkid -c /dev/null"

---

### Post by Mark Phelps on 2010-02-09
Don't know what you mean by "Can't see the partition" but if there is a filesystem problem on an NTFS volume, Ubuntu will refuse to mount it.

Did you do another chkdsk AFTER you removed those files? If not, I would boot back into MS Windows and do another chkdsk.

IF you keep getting NTFS filesystem problems, and you're NOT updating or writing files in that partition from inside Ubuntu, I would suspect a failing hard drive.

---

### Post by viodelin on 2010-02-09
> **john newbuntu said:**
> Try unistalling "ntfs-3g" from synaptic (system->admin->synaptic package manager) and reinstalling it.  If that does not help, post the output of "cat /etc/fstab" from a terminal and "sudo blkid -c /dev/null"

Tried reinstalling ntfs-3g, didn't work.
Here is the contents of fstab

maria@labonita:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=2190c68d-26f2-464f-a506-7df412149060 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=f6da9d35-25e5-4536-b822-05d8ca485de1 /home           ext3    relatime        0       2
# /dev/sda7
UUID=caa8b486-39ce-453f-96f3-2ae7ce49c0f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sda5    
UUID=F6845C55845C1B07    /media/elotrolado    ntfs    user,uid=1000,gid=1000,iocharset=iso8859-1    1    0
# /dev/sda11 
UUID=6F4E-872D /media/FAT32DATA vfat user,uid=1000,gid=1000,iocharset=iso8859-1 1 0

and here's blkid

/dev/sda1: UUID="7230C41D30C3E667" LABEL="Local Disk" TYPE="ntfs" 
/dev/sda5: UUID="F6845C55845C1B07" LABEL="elotrolado" TYPE="ntfs" 
/dev/sda6: UUID="2190c68d-26f2-464f-a506-7df412149060" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="caa8b486-39ce-453f-96f3-2ae7ce49c0f1" 
/dev/sda8: UUID="f6da9d35-25e5-4536-b822-05d8ca485de1" TYPE="ext3" 
/dev/sda9: UUID="F66C24FD6C24BA6F" LABEL="PagefileXP" TYPE="ntfs" 
/dev/sda10: LABEL="WIN98PROGS" UUID="25D8-6A04" TYPE="vfat" 
/dev/sda11: LABEL="FAT32DATA" UUID="6F4E-872D" TYPE="vfat"

???

---

### Post by viodelin on 2010-02-09
> **Mark Phelps said:**
> Don't know what you mean by "Can't see the partition" 

I mean that it did not seem to exist in "places". Now it exists, but it won't mount.

 
> **Mark Phelps said:**
> Did you do another chkdsk AFTER you removed those files? If not, I would boot back into MS Windows and do another chkdsk.

I have done so now. did a chkdsk -f so it would fix the errors (without the -f it simply said there were errors, didn't say what they consisted of. I got a screenshot of the result but unfortunately I can't copy it here - or don't know how. Anyhow it simply says "Windows has made corrections to the file system" and then gives all the stats on disk usage, with 0 bad sectors.

I've come back to ubuntu and it still can't mount the partition :-(

Perhaps I ought to look into that "external FUSE library"...

thanks for trying to help. Any more ideas will be appreciated.

---

