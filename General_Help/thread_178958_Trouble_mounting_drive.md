---
title: "Trouble mounting drive"
date: 2006-05-18
forum: General Help
---

### Post by bl0w on 2006-05-18
Hi, 
I've added a new drive to my system and am having trouble accessing the drive after mounting it. I've got the following entry in /etc/fstab:
> /dev/sda2 /mnt/sata1 xfs auto,user,exec,rw,async 0 0

But when I try and access /mnt/sata1 I get an error "Permission Denied" error. I've tried sudo chmod 666 sata1. But with no effect.

Any advice is appreciated.
B

---

### Post by Falados on 2006-05-18
Try doing "man mount" to look for xfs mount options

Its probably something like
umask=0666 or user=666 or something similar.

---

### Post by bl0w on 2006-05-18
Thanks for the quick reply, I've tried experimenting with some arguments but it hasn't helped.
If I just call mount with no arguments it lists the mounted partitions, for the new partition it lists the following - does this give any indication of why I can't access it?: 

> /dev/sda2 on /mnt/sata1 type xfs (rw,nosuid,nodev)

---

### Post by Falados on 2006-05-18
Hmm, You could try un mounting it then

specify the 'users' option, and then mount it as a normal user.
Perhaps it will set the permitions for your particular user/group (might also want to specify the *suid* option?)

---

### Post by bl0w on 2006-05-18
Here's the answer:

Permissions of 666 for a directory is wrong. The execute bit acts as a access bit for directories. If you want /mnt/sata1 to be writeable by everybody try permissions of 1777:

# chmod 1777 /mnt/sata1

---

