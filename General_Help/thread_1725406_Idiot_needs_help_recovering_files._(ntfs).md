---
title: "Idiot needs help recovering files. (ntfs)"
date: 2011-04-09
forum: General Help
---

### Post by shoot2kill on 2011-04-09
Hi, I just made a really stupid mistake, which I think I am going to regret.

I was editing my fstab to automount a couple of storage drives on start up, and I wanted to test which drive was which.

I did a simple
```
mkdir x && sudo mount /dev/sdb1 x && ls x
```

I determined which hard drive it was, and updated my fstab.

[stupidity]
I then, without thinking issued
```

sudo rm -r x

```
My initial thought was to get rid of the folder i have just created, but forgot top umount first.

I heard the disk making a noise, and QUICKLY (3 secs) hit CTRL+C. this stopped the process. 
[/stupidity]

I then looked at the HDD, and according to ubuntu, it was empty.

This hard drive had ~450GB of data on it, and im fairly sure only some of it will have been deleted/corrupt in 3 seconds, and just the file headers have been removed.

If anyone can help, Please.

P.S., it was NTFS

---

### Post by kinderen on 2011-04-09
look at this site this might help:
[http://www.cyberciti.biz/tips/linux-recover-deleted-files-with-lsof-command.html](http://www.cyberciti.biz/tips/linux-recover-deleted-files-with-lsof-command.html)

---

