---
title: "Pure FTP and filesystem permissions"
date: 2010-05-11
forum: General Help
---

### Post by ^_Pepe_^ on 2010-05-11
Hi all,

I need to set up a ftp server for some of my friends to acce/ss to one of my disks (filesystem, really).

I'd like to do it through a gui, and I found this [https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP) help file, that works quite fine, and lets me customize the "virtual" users.

I've created "ftpuser" in "ftpgroup" as explained, and everything works with /home/ftpuser, that I can manage to change onwership to ftpuser as explained.

The problem is that I want the users to get their home directory in other disk /media/OTHERDISK/xx.ftpuser, and /media/OTHERDISK is a filesystem owned by root. I'm not able to make .../xx.ftpuser owned by ftpuser at all and I get a login error. 

This threads doesn't solve even the error is the same:
[http://ubuntuforums.org/showthread.php?t=958972](http://ubuntuforums.org/showthread.php?t=958972)
[http://ubuntuforums.org/showthread.php?t=1079223](http://ubuntuforums.org/showthread.php?t=1079223)


So...this issue is regarding permissions, not ftp server... :)

Any help would be appreciated.

Regards,
^_Pepe_^

---

### Post by ^_Pepe_^ on 2010-05-11
I'm very sorry. I've restarted the process from the beginning and everything worked ok, even with root-owned folders.

But, /home/ftpusers folder MUST exist and be onwed by "ftpuser"

Rgds

---

