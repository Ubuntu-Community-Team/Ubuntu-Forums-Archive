---
title: "Anyone seen this one yet? strange problem when trying to boot..."
date: 2009-07-08
forum: General Help
---

### Post by Erik765 on 2009-07-08
Hi there,
I recently upgraded from Intrepid to Jaunty and all went well, except now when I reboot, I get the slider bar moving from side to side and it used to do that a couple times then start at the left and fill up to the right, then go to the log in screen.

Now, it just moves from side to side and never starts to actually fill up and then I get this:

> Straing up ...
Loading, please wait...
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/b4f065d9-97b3-44ef-9971-b75bb6ba7fa9 does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initranfs) [   60.576010] ata6: softreset failed (device not ready)
[   65.608008] ata6: softreset failed (device not ready)

Then it sits at a prompt. If I type 'exit' it will continue to boot and my hard drive light will stay on solid for several hours, and the computer will seem to work normally.

The uuid listed is my main partition where I'm booting from (don't have a seperate boot partition).

What does all this mean? Any ideas what could have caused it? Is there anything I should be worried about or any way I can fix it?

Let me know if you need more information to help with a remedy.

Thanks in advance ;)

btw, pulseaudio sux!

E

---

### Post by vikkikanhaua on 2009-07-08
just check in ur fstab that the uuid of partitions listed & present uuid of partitions is same.might be u hve formatted a partition & it's uuid is changed which is causing the problem
to check current uuid, write in terminal
> blkid

---

