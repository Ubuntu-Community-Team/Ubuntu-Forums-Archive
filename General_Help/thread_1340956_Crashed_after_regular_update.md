---
title: "Crashed after regular update"
date: 2009-11-29
forum: General Help
---

### Post by bimaljr on 2009-11-29
Hello

I have installed kubuntu 9.10 3 days ago.

I have updated my system today morning. After update it requires to restart. After restart it doesn't start.

I have then start in "recovery mode" to check what's the problem.
Here is what I see :
> Begin: Waiting for root file system..
Done
Gave up waiting for root device.
Common Problems
- Boot args (cat /proc/cmdline)
- Check rootdelay (did the system waiting for ling enough)
- check root (did the system wait for right device)
- Missing mdules (cat /proc/modules; ls /dev)
[COLOR="Red"]Alert! /dev/disk/by-uuid/2ce321d3....5b does not exist.[/COLOR]
Dropping to a shell!
BusyBox v 1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)

Here I think the problem with RED file in above box. I think the uuid would changed. But I don't know what happend on update.

How to solve this problem ?

Thanks.

---

