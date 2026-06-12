---
title: "strace tells that gnome-terminal doesn't access it profile configuration files"
date: 2012-02-06
forum: General Help
---

### Post by zertsekel on 2012-02-06
Hi all,

I was trying to see configuration file is used by gnome-terminal by using strace, but no access to gnome-terminal profile file is seen by strace:

$ strace -o strace.txt gnome-terminal
$ grep gconf strace.txt 
open("/usr/lib/libgconf-2.so.4", O_RDONLY) = 3

But gnome-terminal configuration file is here (the usual place);
$ ls ~/.gconf/apps/gnome-terminal/profiles/
Default  %gconf.xml  Profile0  Profile1

I am using this Ubuntu:
$ cat /etc/issue
Ubuntu 11.10 \n \l

$ uname -a
Linux zk320 3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:44:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Thanks,
--- KostaZ

---

