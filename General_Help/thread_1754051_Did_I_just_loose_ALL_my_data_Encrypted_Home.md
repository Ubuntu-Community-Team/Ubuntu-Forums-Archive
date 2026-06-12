---
title: "Did I just loose ALL my data? Encrypted Home"
date: 2011-05-09
forum: General Help
---

### Post by xandr55 on 2011-05-09
So I was trying to mount my home folder from a liveCD to back it up before a new install by following the following. After mounting I did something really stupid and accidentally deleted a .ecryptfs file. I tried to recover it (as I deleted it in nautilus thought that it would therefore be in trash and not rm'd) but no avail. When I rebooted my encrypted home wouldn't mount, I just see the same thing I do when I look at that partition from the liveCD. Any ideas on regenerating this information to get all my documents back? Bellow are the instructions that I was trying to follow but couldn't get to work.

Thank you very much ahead of time.

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709)

---

### Post by xandr55 on 2011-05-09
EDIT: Posted this to the ecryptfs mailing list and received a prompt reply that the new version of ubuntu (and therefore probably mint) has a utility called by ecryptfs-recover-private that does a deep search of mounted filesystems for any .Private directories, and then attempts to recover them. All that is needed is your (in my case logon) mount password and everything goes smoothly, even mounts it to a read-only point on /temp so that you can perform file-recovery and not mess anything up (like I had) worked like a charm. Seriously just make a liveCD of ubuntu Natty, or presumably mint11, mount your hard-drive, open a terminal, enter sudo ecryptfs-recover-private, enter your logon password and you are set to go! Thanks Dustin Kirkland!.

His original post:
If you accurately recorded your mount passphrase, you should be able
to follow the instructions at:
 * [http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)
and recover your data.

Dustin

-Xander

---

