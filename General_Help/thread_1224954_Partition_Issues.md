---
title: "Partition Issues"
date: 2009-07-28
forum: General Help
---

### Post by Zero++ on 2009-07-28
This is really more of a windows question but here it goes.

I have 2 hard drives in my Ubuntu / XP system. A 120gig with Windows (NTFS) and a 250 gig with Ubuntu. I decided to create a 45 gig NTFS partition on my Ubuntu drive so I could put my music files there so my windows and linux music players could see them and use them. 

Ubuntu sees it just fine and I even have it mount on startup (via fstab) but windows just won't see it. It is located at the end of my Linux partition so I'm not sure if this makes a difference or not. 

Again I know the problem is Windows but they don't have the community support that Linux does so I'm asking you guys and gals. Can I get windows to see this drive am I hosed because it is at the end of a drive that Windows does not see properly? 

Thanks Zero++

---

### Post by Hobgoblin on 2009-07-28
The outputs of

```
df
```

and

```
fdisk -l
```

might help.

---

### Post by Zero++ on 2009-07-28
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb5            192243928  39997672 142480748  22% /
tmpfs                   772188         0    772188   0% /lib/init/rw
varrun                  772188       308    771880   1% /var/run
varlock                 772188         0    772188   0% /var/lock
udev                    772188       172    772016   1% /dev
tmpfs                   772188        84    772104   1% /dev/shm
lrm                     772188      2192    769996   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb1               964500     56444    859060   7% /boot
/dev/sdb7             47271228  24690128  22581100  53% /media/Music
/dev/sdc1            156250144  78082784  78167360  50% /media/WD Passport
tmpfs                   772188      2192    769996   1% /lib/modules/2.6.28-14-generic/volatile

---

### Post by Hobgoblin on 2009-07-29
```
sudo fdisk -l
```

might help.

[edit] needs sudo

---

