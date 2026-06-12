---
title: "installed&gt;&gt;uninstalled&gt;&gt;installed Now missing files and won't open"
date: 2012-09-28
forum: General Help
---

### Post by 777funk on 2012-09-28
I tried a program called Darktable and removed it a while back. I just decided to give it another go and installed it. I open the program and nothing happens. I open in the Terminal and here's what it gave:

```

nick@NickUbuntu:~$ darktable
[init] could not open database `library.db'!
[init] check your /apps/darktable/database gconf entry!
```


Any idea on where to look?

---

### Post by 777funk on 2012-09-28
Just had a different error. Can't seem to get this to install properly now.

> nick@NickUbuntu:~$ darktable
[defaults] found a 32-bit system with 3031880 kb ram and 2 cores
[defaults] setting very conservative defaults
[init] could not find database `library.db'!
[init] maybe your /home/nick/.config/darktable/darktablerc is corrupt?
[init] try `cp /usr/share/darktable/darktablerc /home/nick/.config/darktable/darktablerc'
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
/home/nick/17101: No such file or directory.
/usr/share/darktable/gdb_commands:1: Error in sourced command file:
No stack.
an error occured while trying to execute gdb. please check if gdb is installed on your system.
Segmentation fault (core dumped)


OK Solved. It wouldn't let me do this:
> cp /usr/share/darktable/darktablerc /home/nick/.config/darktable/darktablerc

because the folder already existed (even though I couldn't see it and had "View Hidden Folders" checked... but went into terminal and Removed the folder then copied as the error said and it worked!

---

