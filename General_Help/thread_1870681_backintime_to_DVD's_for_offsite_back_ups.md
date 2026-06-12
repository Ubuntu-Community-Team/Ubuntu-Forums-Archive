---
title: "backintime to DVD's for offsite back ups"
date: 2011-10-27
forum: General Help
---

### Post by Jenkins1 on 2011-10-27
Hello all,

I have been using backintime for a while to back up my files to a second hard disk. The only system that I am missing is some of site backups. I am unable to place a pc/server in someone else's house and am not keen on online solutions. So have decided to burn it to DVD's which will be stored in another location. It is going to need a lot of DVD's initially but hopefully it will only need one or two disks a month. 

I have a long list of folders as below. Using disk usage analyser they come to ~100GB. I decided that I would use rar to split them into dvd size archives.
```
rar a -ol -m5 -v4450m /media/extra-home/archive.rar *

```

However using this command the total size of files is greater than 100GB. I think its down to the way backintime uses links. 

I also tried running the command without the ```
-ol
``` flag but it just filled my ram up and had an error of "To many symbolic links"

My ultimate aim is to automate the process so my computer just prompts for a DVD once a month. Any suggestions on how to get rar working or any other method for spliting the files up into 4.5GB parts are welcome.

Thnaks

---

### Post by Jenkins1 on 2011-11-02
Bump

---

