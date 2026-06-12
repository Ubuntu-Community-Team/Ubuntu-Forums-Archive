---
title: "Back In Time"
date: 2010-05-18
forum: General Help
---

### Post by daz4126 on 2010-05-18
Hi,

I'm using Back In Time to backup my home directory to a second hdd that is mounted at /media/backup

The trouble is, I can do this using Back In Time (Root), but not using Back In Time without the root option. This is definitely a permissions issue - it can't write to the folder, but when I checked by right clicking on the backup directory and looking at the permission tab, it said I was the owner.

Is there anything else I need to change the setting of?

cheers,

DAZ

---

### Post by 2hot6ft2 on 2010-05-18
There are hidden configuration files and folders that are owned by root in /home. You can back up other things as a regular user using it.
:popcorn:

---

### Post by daz4126 on 2010-05-21
Thanks for the reply 2hot6ft2, but I'm not trying to back up /home, just my part of the home directory /home/daz

And the error message is specifically saying that it can't write to /media

Anybody know why?

cheers,

DAZ

---

