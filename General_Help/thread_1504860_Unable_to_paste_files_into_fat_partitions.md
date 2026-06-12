---
title: "Unable to paste files into fat partitions"
date: 2010-06-08
forum: General Help
---

### Post by ranjithnair on 2010-06-08
I am using the following code in /etc/fstab. The problem is that i am not able to paste anything into /dev/sda4 and /dev/sda5 which are vfat files.....How can I edit fstab so that i can paste files into them.....

[COLOR="Red"]/dev/sda4 /media/Movies vfat defaults 0 0[/COLOR]

/dev/sda6 /media/Songs ntfs defaults 0 0

[COLOR="Red"]/dev/sda5 /media/Software vfat defaults 0 0[/COLOR]

/dev/sda2 /media/WINXP ntfs defaults 0 0

---

### Post by WorMzy on 2010-06-08
Here comes a barrage of questions. :)

Do you get an error? Post it here.

Can you create new files on the partitions?

Can you rename existing files?

Are the partitions full?

Are the partitions on a removable pen drive with a read-only hardware mode activated? (Some pen drives have a switch on their side which makes the drive read-only)

What size files are you trying to copy?

---

### Post by Morbius1 on 2010-06-08
This is actually an excellent example of why you should always explicitly list the umask in every fstab entry for a windows filetype.

"defaults" will mount a vfat filetype to mode = 0755. Read / write to owner and read only to everyone else. Unfortunately root is the owner so only root can read / write.

You've got three choices:

(1) Make it accessible to everyone:
>  [COLOR=Black]/dev/sda4 /media/Movies vfat defaults,umask=000 0 0[/COLOR](2) Take possession of the mount point:
>  [COLOR=Black]/dev/sda4 /media/Movies vfat defaults,uid=1000 0 0[/COLOR](3) Do it the way Ubuntu would do it if you told it to mount these during the install:
> [COLOR=Black]/dev/sda4 /media/Movies [/COLOR]vfat utf8,umask=007,gid=46 0       1umask=007 - read / write to owner and group and no one else
gid=46 - the group 46 represents "plugdev". All local login users are members of the plugdev group by default. So all local login users will have R / W access.

---

