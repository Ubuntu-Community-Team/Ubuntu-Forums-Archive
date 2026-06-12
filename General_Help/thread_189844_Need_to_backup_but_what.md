---
title: "Need to backup: but what?"
date: 2006-06-05
forum: General Help
---

### Post by .t. on 2006-06-05
I need to backup my system, so I can re-install, as I cannot move my ext3 partition to another area on the disk. Of course, I need to backup my /etc and /home partitions, but is there anything else. I have a list of all installed packages, so if I were to just backup those files, re-install the system and all the packages, copy back the files, would I be alright?

---

### Post by .t. on 2006-06-06
*Bump*

---

### Post by aysiu on 2006-06-06
[QUOTE=.t.]I need to backup my system, so I can re-install, as I cannot move my ext3 partition to another area on the disk.[/QUOTE] Who says you cannot move it to another area? [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

Of course, if you do move it, you'll have adjust the /etc/fstab and /boot/grub/menu.lst to reflect the changes.

---

### Post by ifokkema on 2006-06-06
[QUOTE=.t.]I need to backup my system, so I can re-install, as I cannot move my ext3 partition to another area on the disk. Of course, I need to backup my /etc and /home partitions, but is there anything else. I have a list of all installed packages, so if I were to just backup those files, re-install the system and all the packages, copy back the files, would I be alright?[/QUOTE]

Well, with your /home you got your personal settings, with your /etc you got your system-wide settings. I can only suggest other things to consider:
- Do you use MySQL? Backup the database from /var/lib/mysql.
- Do you use crontabs?
- Do you have mail in directories outside your home directory, such as /var/mail?

Hope this helps.

Ivo

---

### Post by .t. on 2006-06-06
PartImage looks interesting, but I'd prefer to do a fresh install (keep my system clean). And yes, I do use crontabs - is there anything I need to know? Should I just add my /var directory to my backup list?

---

### Post by ifokkema on 2006-06-06
[QUOTE=.t.]PartImage looks interesting, but I'd prefer to do a fresh install (keep my system clean). And yes, I do use crontabs - is there anything I need to know? Should I just add my /var directory to my backup list?[/QUOTE]

You can do so, although lots of it's contents is probably of no use to you. A copy of your crontabs (set using crontab -e) can be found in:

```
/var/spool/cron/crontabs
```

Hope this helps.

Ivo

---

### Post by .t. on 2006-06-06
Right, so I am backing up /home, /etc and /var. Cheers, I'll do the install soon.

---

