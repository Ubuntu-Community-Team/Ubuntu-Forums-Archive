---
title: "plymouthd process always running"
date: 2010-06-17
forum: General Help
---

### Post by Zeemvel on 2010-06-17
If I run top, there's a process plymouthd always running, often taking a few percents of CPU.

I found that "plymouth" would be a splash screen. My PC is booted already though, I don't need a splashscreen once it has booted.

Is this a bug?

How can I get rid of this process that always uses %CPU?

Ubuntu version 10.4.
 
Thanks.

---

### Post by _Mark_ on 2010-06-17
I don't know exact details, but have read on the forums that a lot of other "stuff" depends on plymouth it's not just a splash screen

Sure someone else will be able to give more details

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) halfway down the first post bootup/ plymouth section
> Plymouth now has a hard dependency on mountall thus trying to remove Plymouth would remove half the OS.

---

### Post by Zeemvel on 2010-07-01
Hi, this is still occuring, whenever my system is restarted, the plymouthd process is there and stays there. Not just during the boot, no, during the whole day or week I'm working on this computer. And it's always running at 5% CPU.

What options do I have to disable this? What exactly can I do? Which config files can I change? Can I somehow auto-kill it after every boot?

The process requires root access (sudo) to be killed.

I'd like to treat the symptoms, or the cause if possible.

I don't want to manually kill it after every boot, I'd like it to automatically go away somehow :)

Thanks.

---

### Post by backwoodsman on 2011-11-17
I know this is a very old thread, but there was no solution posted, and I haven't found one elsewhere.  plymouthd always runs and takes over 5% of the CPU.  The machine in question is old and slow, and I really can't afford to have it using up that much CPU.  I can kill it manually, but how can I kill it automatically, or make it kill itself?

[EDIT] Found the following fix, which involves editing /etc/default/grub; now plymouthd is still running, but using no CPU.  That machine is 1.2ghz and the difference in speed is quite noticeable.  I'll be applying this fix to faster machines as well, when I install Ubuntu.  But I'd still like to find a solution that gets rid of plymouthd altogether.

[http://www.techytalk.info/disable-plymouth-show-grub-menu-ubuntu-linux/](http://www.techytalk.info/disable-plymouth-show-grub-menu-ubuntu-linux/)

---

