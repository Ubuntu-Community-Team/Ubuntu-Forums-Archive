---
title: "backup system program"
date: 2006-02-18
forum: General Help
---

### Post by harty83 on 2006-02-18
Howdy,

So I've searched through the forums and am not finding what I want for a backup utility.

I've looked at konserve but it lacks the option to exclude specific directories.

Here is what I'm looking for:
*Back up my entire system to an external and a network share
*A gui interface (if possible; kde or gnome)
*The option to exclude specific directories or files (reason being that otherwise it will recursively backup my external that I'm backing up to!)
*Backup will save all attributes of files/folders (permissions, owner, timestamps, etc)
*Autobackup feature (set time and date to backup and it will automatically start)

Know of anything out there that matches that criteria?

Thanks!

---

### Post by linuxden on 2006-02-18
You could TAR all your directories to a file called backup.tgz... And use the exclude option by --exclude /all/the/directories/you/dont/want...

---

### Post by harty83 on 2006-02-18
> You could TAR all your directories to a file called backup.tgz

I've thought of that.  But what I would like is to have my server backed up every night without me having to manually start it.

---

