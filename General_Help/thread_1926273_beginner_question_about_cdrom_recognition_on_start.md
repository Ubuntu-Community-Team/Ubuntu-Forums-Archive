---
title: "beginner question about cdrom recognition on startup in graphical interface..."
date: 2012-02-16
forum: General Help
---

### Post by johnk26 on 2012-02-16
Simple question. In Ubuntu 11.10 :    CDROM does not come up automatically when the system boots.   If I go into a terminal window I can:

[LIST]
[*] sudo mount /dev/sr0 /media/cdrom
[/LIST]
 and it mounts AND it appears in the HOME graphical interface COMPUTER list (though it is owned by root it is accessible).   If I add to /etc/fstab a line that has 

[LIST]
[*]    /dev/sr0 /media/cdrom udf,iso9660 user, noauto, exec, utf8  0  0
[/LIST]
upon reboot the system doesn't like it.. and asks to skip or fix manually... How do i get this cdrom recognized automatically at startup or at least when a valid disk is in place.    this is a fresh install on an old laptop.  Have a screwed up the device spec in fstab?  Is there someplace else to do this?  Is there a startup file i need to install a mount command in?

sorry but i have been through scores of online help pages and none of the suggestions seem to work and this seems so basic...    thx

---

### Post by dcstar on 2012-02-16
> **johnk26 said:**
> Simple question. In Ubuntu 11.10 :    CDROM does not come up automatically when the system boots.
..........


So what?, the Desktop you are using automatically mounts it when **you** put in a disk.

---

### Post by johnk26 on 2012-02-16
No, that is exactly the problem. It does not.  The only time the cdrom appears in the 'HOME' files listing is when i mount it via terminal with sudo mount....  Thanks anyway... 

EDIT: 

So, given the somewhat sarcastic and useless response of DCSTAR, it seems that this is not such a useful or friendly forum and I'll go through the trouble of building another flavor of UNIX.    

When the user interface doesn't do what it is supposed to do, I kind of expect that is not a question that should be dismissed out of hand.  I wish you all the best with your forum and won't bother you again.

---

