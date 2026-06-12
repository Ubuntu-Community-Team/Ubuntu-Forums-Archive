---
title: "Disappearing Disk Space"
date: 2009-10-19
forum: General Help
---

### Post by aftermgates on 2009-10-19
Last night I was auditing my wireless connection for several hours using aircrack-ng. This morning I turned my computer on and noticed that my available disk space had somehow gone to 0 bytes; last I remember, I had ~1GB. I really don't understand how it could have happened. It might not necessarily be because of aircrack-ng but that is the only thing I had used.
Also, my Compiz settings are not functioning, which I suppose is due to the lack of disk space.

I can give any other information that is needed.

---

### Post by iMisspell on 2009-10-19
Im not saying this is what happend to you (or this link will help you), but months ago i restarted a windows machine which had a 1TB drive only to find it shrunk to 33MB (on reboot).
Have no idea what caused it, but the following link fixed it and no data was lost.

[http://blog.atola.com/restoring-factory-hard-drive-capacity/#comment-4148](http://blog.atola.com/restoring-factory-hard-drive-capacity/#comment-4148)

Maybe some info there will help lead you in some kind of direction.
good luck...

_

---

### Post by lidex on 2009-10-19
You"ll want this info:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by P4man on 2009-10-19
aircrack logs all traffic it snoops afaik.

---

### Post by aftermgates on 2009-10-19
After pouring over the forum link, I think I've found the issue. sort of. /var/log is almost 2GB somehow. 
```
sudo du -h /var/log
``` gave me this:
```
michael@ubuntu:~$ sudo du -h /var/log
[sudo] password for michael: 
64K	/var/log/gdm
60K	/var/log/cups
784K	/var/log/installer
4.0K	/var/log/unattended-upgrades
4.0K	/var/log/samba
64K	/var/log/apt
800K	/var/log/dist-upgrade
552K	/var/log/clamav
4.0K	/var/log/news
80M	/var/log/kismet
4.0K	/var/log/apparmor
5.3M	/var/log/ConsoleKit
12K	/var/log/fsck
1.9G	/var/log
```
So /var/log is full of files, but the link doesn't give enough instruction. I would love to determine which program is generating the log files and try to change its behavior, but I don't know how to go about that.
Attempting to delete any files from /var/log, such as a .gz, results in a permission denied message.

---

### Post by arrange on 2009-10-19
Can you see any large files in the /var/log directory?

Or run```
find /var/log -size +10M
```

---

### Post by P4man on 2009-10-19
> **aftermgates said:**
> 
Attempting to delete any files from /var/log, such as a .gz, results in a permission denied message.

You need sudo privileges. press alt+F2 and type
```
gksu nautilus
``` 

Then youll be able to delete in /var/log (im pretty sure its aircrack logging there btw)

---

### Post by aftermgates on 2009-10-19
```
michael@ubuntu:~$ find /var/log -size +10M
/var/log/syslog.1.gz
/var/log/syslog.0
/var/log/messages.0
/var/log/messages.1.gz
/var/log/kern.log.1.gz
/var/log/kismet/Kismet-Jan-09-2009-2.dump
/var/log/kismet/Kismet-Jan-09-2009-1.dump
/var/log/kismet/Kismet-Jan-12-2009-2.dump
/var/log/kismet/Kismet-Jan-07-2009-2.dump
/var/log/kern.log.0

```
Then tried
```
michael@ubuntu:~$ find /var/log -size +50M
/var/log/syslog.0
/var/log/messages.0
/var/log/kern.log.0
```

---

### Post by aftermgates on 2009-10-19
> **P4man said:**
> You need sudo privileges. press alt+F2 and type
```
gksu nautilus
``` 

Then youll be able to delete in /var/log (im pretty sure its aircrack logging there btw)
I deleted the logs from /var/log/kismet because I rarely use kismet but I'm unsure about the other files. I don't know what the chances are of deleting something important and I definitely don't want to screw something up.

EDIT: And now I'm back up to 1.3GB of free space from deleting the kismet logs. Not sure how that worked.

---

