---
title: "[SOLVED]Root partition full (sbackup)"
date: 2009-08-27
forum: General Help
---

### Post by Donalb on 2009-08-27
Hey all,

Ok, while searching for a decent backup I reinstalled sbackup in the hope it was fixed (didn't realise it was abandonware).

Anyway, the bug with filling the root partition got me. this happened me once before when trying sbackup but I found the tar.gz files.  

My root partition (10G) was full and I couldn't find the problem this time in the usual place.

It is usually assumed that screwed up backups dump the files to /var/backup
but this wasn't the case.

I have a dual-boot system so I unmounted the Vista and Dell Recovery Partitions, along with all the external media, including the target drive I was trying to backup to, so I could see clearly what was going on.

Then:
```
sudo du -h --max-depth=1 /
```

found the following;

```
6.1M	/bin
717M	/var
4.0K	/srv
59M	/boot
60G	/home
15M	/etc
8.4M	/sbin
4.5G    /media
87M	/opt
12M	/root
16K	/lost+found
0	/proc
8.0K	/mnt
40K	/tmp
0	/sys
3.5G	/usr
3.1M	/dev
475M	/lib
```

Trying```
sudo find / -name '*' -size +500M
```

I found a list including:

```
4.5G    /media/REV 35_/2009-08-27_17.18.44.669165.donals-e6400.ful

```

However that partition was already unmounted and I couldn't remount to delete the file. Looking in /media I could see the drive but couldn't access it obviously since it was unmounted.
I also couldn't launch Nautilus as root. (Can't recall error).

I was afraid to restart as with 100% file system Used I might not be able to get back to GNOME. In which case at least I knew the problem and hoped I could delete the above file (once remounted) from the terminal.

However GNOME did start and I was able to launch root Nautilus this time, and I now had access to the external REV 35 drive and delete the file. 

Everything copacetic.  
 
Hope this helps anyone who runs into this problem and the other solutions don't work, since Simple Backup is still available in the repos and in Applications/ADD/REMOVE with no notification that it causes this problem (and the fix to not proceed if external media is not present doesn't work) so people are bound to continue to install it.

rgds

---

