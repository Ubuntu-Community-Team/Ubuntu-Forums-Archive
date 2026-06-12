---
title: "Limiting Cached Memory in Ubuntu"
date: 2011-06-13
forum: General Help
---

### Post by dmiles813 on 2011-06-13
Folks -

I'm looking for a way to limit the kernel cached memory?  Before everyone asks, our Ubuntu boxes are Virtual Machines on a shared server.  As such, cached physical memory can hurt the VM server in whole.  To "play nice" on the server, we can't have each Ubuntu VM session caching 4-6 gigs of RAM each.  I would like to limit the cached memory to say 2GB above what is currently being utilized?  That should not hurt performance that much.

Does anyone know of a means to do this?  I'd like to tune the kernel, as opposed to other methods I have found online using sync/echo.

I have never tuned a linux kernel - so step-by-step instructions would be greatly appreciated.

If someone has a better idea, I'm all ears.

Here is what one of the servers looked like before a reboot...


user@server:~$ uname -a
Linux xxx 2.6.32-32-server xxx x86_64 GNU/Linux

user@server:~$ free -m
          total   used   free  shared  buffers  cached
Mem:      7750    6722   1028       0       31    [COLOR="Red"]5901[/COLOR]
-/+ buffers/cache: 790   6960
Swap:     3374       0   3374

---

