---
title: "external HD corruption"
date: 2011-02-03
forum: General Help
---

### Post by bradhaack on 2011-02-03
I have an external HD that I use for backup, using rsnapshot.  It is a 100 Gig drive, but now du or rsnapshot du shows that it using Petra Bytes,  20929340526888 to be exact.  df still shows reasonable numbers.
There is one directory that seems to be corrupted, since it's several months old I tried to delete it, but even using sudo rm -rf it says Operation not permitted.  It is an ext4 encrypted disk, but is unlocked.
Suggestions?

---

### Post by CharlesA on 2011-02-03
It's probably counting the hard links.

Are you using du -h?

---

### Post by bradhaack on 2011-02-03
It doesn't matter if I use -h or not, did you mean -H?

---

### Post by bradhaack on 2011-02-03
I ran fsck, & that seems to have fixed the size problem.  But one of the directories is still corrupted and & can't even delete it.

ls -l
total 72
drwxr-xr-x  15 root root   4096 2011-02-02 19:09 daily.0
drwxr-xr-x  15 root root   4096 2011-01-12 12:39 daily.1
drwxr-xr-x  15 root root   4096 2011-01-12 12:39 daily.2
drwxr-xr-x  15 root root   4096 2011-01-12 12:39 daily.3
drwxr-xr-x  15 root root   4096 2011-01-12 12:39 daily.4
drwxr-xr-x  15 root root   4096 2011-01-12 12:39 daily.5
drwxr-xr-x  15 root root   4096 2011-01-12 12:39 daily.6
drwx------ 200 root root  16384 2010-10-01 18:51 lost+found
drwxr-xr-x  15 root root   4096 2010-12-03 14:24 monthly.0
drwxr-xr-x  16 root root   4096 2010-10-14 20:23 monthly.1
dr---wx-wx   2 9327 36968  4096 1970-12-05 20:09 monthly.2
drwxr-xr-x  15 root root   4096 2011-01-12 12:39 weekly.0


sudo -s rm -rf monthly.2
rm: cannot remove `monthly.2/vmlinuz': Permission denied
rm: cannot remove `monthly.2/home': Permission denied
rm: cannot remove `monthly.2/cdrom': Permission denied
rm: cannot remove `monthly.2/initrd.img': Permission denied

---

### Post by CharlesA on 2011-02-03
-h is human readable.

The permissions are wrong. You'd need to chown it so it has the correct owner and group. Then chmod it to get the permissions correct.

---

### Post by bradhaack on 2011-02-03
Already tried that.

sudo chown root monthly.2
chown: changing ownership of `monthly.2': Operation not permitted

Same thing for chmod
What does it mean that the owner is 9327??  Why can't sudo change owner or permissions?

dr---wx-wx   2 9327 36968  4096 1970-12-05 20:09 monthly.2

---

### Post by CharlesA on 2011-02-03
It must have had the owner with that UID.

The problem is that the permissions are hosed up.

Use sudo -i to get to a root prompt and see if you can run this:

```
chmod -R 777 monthly.2
```

---

### Post by bradhaack on 2011-02-03
Nope, still same result:

root@brad-desktop:/media/Maxtor-1# chmod -R 777 monthly.2
chmod: changing permissions of `monthly.2': Operation not permitted

---

### Post by bradhaack on 2011-02-03
OK, making progress w/ 
chattr -i

---

