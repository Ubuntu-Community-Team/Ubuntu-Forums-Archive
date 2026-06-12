---
title: "Gzip/rsync to NTFS partition"
date: 2011-06-01
forum: General Help
---

### Post by WildZontar on 2011-06-01
I recently moved to Ubuntu full-time. When I was on Windows 7, I had a nice backup arrangement that copied the vital bits to an external NTFS drive. 

What's the best way to backup an Ubuntu system to this NTFS drive? I was considering gzip (to preserve permisisons and ext4 specifics) and then rsync'ing the .tar.gz file to an NTFS partition, but have no idea how to do either properly.

---

### Post by ruffEdgz on 2011-06-01
I would first see if you can change that NTFS drive to ext3 or even better ext4 ;)

I would have to agree with you that rsync and gzip is a good way to complete the backups. I think picking the tools are easy but where are the backups going? On another partition? On a separate drive? in the cloud (hehehe I had to say it) or other machine?

I just did a google search for "backup with rsync" and found some nice sites that have some examples but if you give some more info, I or someone else can give their input on creating a script for you.

Once that script is created, I would just figure out when you want the backups to run and then edit your or root's crontab:
```

crontab -e
(users)

or

sudo crontab -e
(roots)

```

From there you will want to edit the file by following these simple rules:
```

*    *    *    *    *  command to be executed
&#9516;    &#9516;    &#9516;    &#9516;    &#9516;
&#9474;    &#9474;    &#9474;    &#9474;    &#9474;
&#9474;    &#9474;    &#9474;    &#9474;    &#9474;
&#9474;    &#9474;    &#9474;    &#9474;    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472; day of week (0 - 7) (Sunday=0 or 7)
&#9474;    &#9474;    &#9474;    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; month (1 - 12)
&#9474;    &#9474;    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; day of month (1 - 31)
&#9474;    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; hour (0 - 23)
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; min (0 - 59)

```
Reference = [http://en.wikipedia.org/wiki/Cron#Predefined_scheduling_definitions](http://en.wikipedia.org/wiki/Cron#Predefined_scheduling_definitions)

Hope this helps!

---

