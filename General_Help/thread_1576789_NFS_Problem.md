---
title: "NFS Problem"
date: 2010-09-17
forum: General Help
---

### Post by JKyleOKC on 2010-09-17
I'm exporting the entire directory tree of one machine specifically to another, but on the receiving machine the exported /home directory (/net/xubuntu/home) shows up as empty. All other directories show their full content; only /home seems to be blocked. It actually contains two user directories plus lost+found, and has r-x permissions for everyone. Anyone have any ideas what could be causing this?

Here are the listings. First, the exported machine:```
jk@xubuntu:~$ ll /home
total 32
drwxr-xr-x  5 root root  4096 2010-08-09 19:45 ./
drwxr-xr-x 24 root root  4096 2010-09-06 08:35 ../
drwxr-xr-x 30 jk   jk    4096 2010-09-17 08:41 jk/
drwxr-xr-x 22 jo   jo    4096 2010-09-16 21:54 jo/
drwx------  2 root root 16384 2010-08-09 19:25 lost+found/
jk@xubuntu:~$ grep nohide /etc/exports
/	192.168.0.2(rw,no_root_squash,no_subtree_check,nohide,sync)
```
Next, the receiving machine (which is at 192.168.0.2):```
jk@mehitabel:~$ ll /net/xubuntu/home
total 8
drwxr-xr-x  2 root root 4096 2010-08-09 19:25 ./
drwxr-xr-x 24 root root 4096 2010-09-06 08:35 ../

```

---

### Post by spjackson on 2010-09-18
/home also needs to be in /etc/exports with the nohide option. Once you've added that, you will probably need to remount /net/xubuntu on the other machine.

---

### Post by JKyleOKC on 2010-09-18
It worked, but I'm still puzzled. I can access the subdirectories in /var/log/fsck without having them exported separately, but not those in /var/home although they have the same permissions. Inconsistencies of this sort bother me!

Many thanks for the response. At least I can now administer the machine remotely, and transfer files between the systems easily.

---

