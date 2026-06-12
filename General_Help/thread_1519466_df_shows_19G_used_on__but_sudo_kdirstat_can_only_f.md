---
title: "df shows 19G used on / but sudo kdirstat can only find 6G? Where did 13G go?"
date: 2010-06-28
forum: General Help
---

### Post by motin on 2010-06-28
I have a fairly clean Ubuntu Karmic install on a 24G partition dedicated only for /. 

df -h:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              24G   19G  3,7G  84% /
udev                  498M  336K  497M   1% /dev
none                  498M  324K  497M   1% /dev/shm
none                  498M  372K  497M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw
/dev/sda6             331M  112M  202M  36% /boot
/dev/sda8              30G   28G  2,7G  92% /home
/dev/sda9             384G  373G   11G  98% /store

```

I am trying to find out what files and directories that use these 19G, but a "sudo kdirstat" can only account for 6G of used disk-space. There were no errors reported in terminal by kdirstat, only:
```
~$ sudo kdirstat /
[sudo] password for motin: 
Error: "/tmp/kde-motin" is owned by uid 1000 instead of uid 0.

```

One way would be to double-check with "du -m /" but I can't find a way for it not to cross file system boundaries in the ubuntu karmic version. "-d" is reported as the correct parameter for some versions of du but that is not recognized. 

So, how can I find out how the missing 13G is used?

---

### Post by prodigy_ on 2010-06-28
Are you sure that the file system is intact? Try using fsck.

---

