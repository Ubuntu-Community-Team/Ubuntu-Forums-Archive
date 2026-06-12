---
title: "FTP/Symlink Help"
date: 2010-08-19
forum: General Help
---

### Post by Krayons on 2010-08-19
Hi,

I have installed gadmin-proftpd.
I have create various users.

I have given permission to the users.
/home/users/<user>/ (Full access)
/home/shares/ (Download only)

Then I created symlinks in the user directories to shares.
ln -s /home/shares/ /home/users/<user>/shares/

The symlinks work but not through FTP.
I Read some where that if you chroot someone to their home directory they can't see symlinks out of there home directory but even symlinks that are in the users directory don't work.

Any help/suggestions greatly appreciated.

Regards
Kyle

Additional Information:
OS: Ubuntu Server 10.04
FTP Client: FileZilla

Edit:
I see I've posted this in the wrong category.
Please move to Absolute Beginners.

---

