---
title: "ooffice 2.4 fails with 'std::bad_alloc'"
date: 2009-10-13
forum: General Help
---

### Post by duane-tech on 2009-10-13
I can't get openoffice to start. It was working, all that I think has changed are the updates.

I try and get this:
$ ooffice
terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc

The logo comes up and then the error message appears as ooffice aborts.
I tried moving ~/.openoffice* to another directory but didn't help. 

I'm running openoffice 2.4 with Kubuntu 8.04 on a 64bit dual core laptop.

edit: 
Does anyone know how I can trace the problem?

I've tried uninstalling and purging all openoffice.org packages and their dependancies.
"gdb ooffice" doesn't work without rebuilding openoffice. 
"pstree -p" just shows soffice.bin spawning two more soffice.bin processes. 

I ran "lsof" while ooffice was trying to start up. I got:
$ lsof -p $(pgrep soffice|head -1)
COMMAND  PID  USER   FD   TYPE DEVICE    SIZE    NODE NAME
soffice 6727 duane  cwd    DIR  254,4    4096 5365761 /home/duane
soffice 6727 duane  rtd    DIR  254,0    4096       2 /
soffice 6727 duane  txt    REG  254,0  100856  376854 /bin/dash
soffice 6727 duane  mem    REG  254,0 1436976  155769 /lib/libc-2.7.so
soffice 6727 duane  mem    REG  254,0  127480  155766 /lib/ld-2.7.so
soffice 6727 duane    0u   CHR 136,13              15 /dev/pts/13
soffice 6727 duane    1u   CHR 136,13              15 /dev/pts/13
soffice 6727 duane    2u   CHR 136,13              15 /dev/pts/13
soffice 6727 duane    3r  FIFO    0,5           17790 pipe
soffice 6727 duane    4w  FIFO    0,5           17790 pipe
soffice 6727 duane   10r   REG  254,2    9414   35761 /usr/lib/openoffice/program/soffice

I've reinstalled the dash, and libc6 packages. I also reinstalled libc6-i386, and libc6-dev while I was at it. I've removed and reinstalled all the openoffice packages.

If you could compare this output to your own and comment on any discrepancies, I may learn where the problem is.

Right now, I don't even know where to start figuring out how to fix it.

Any help would be greatly appreciated.

---

