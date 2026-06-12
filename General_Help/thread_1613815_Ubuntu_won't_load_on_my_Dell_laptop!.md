---
title: "Ubuntu won't load on my Dell laptop!"
date: 2010-11-04
forum: General Help
---

### Post by Alternative Solution on 2010-11-04
I have ubuntu loaded on my Dell as the only operating system.  It was working fine.  I would just keep it on all the time, so if there was a problem with it booting previously, I wouldn't have known about it.

I recently installed long overdue updates, and when I restarted the computer, it wasn't able to boot.  I've tried several times, and I always get the same black screen with white text, and a message it gives me. I'll put that message below the dotted line on this post.  There was a series of numbers in there, but I'm not posting those just in case it would be a security risk (not sure if it's a code or something).

Please help!

--------

[FONT=System]mount: mounting /dev/disk/by-uuid/[series of numbers omitted] on /root
failed: Invalid argument
mount: mounting /dev on /root/dev
failed: No such file or directory
mount: mounting /sys on /root/sys
failed: No such file or directory

Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1 ubuntu11) built-in shell (ash)

Enter 'help' for a list of built-in commands.

(initranfs) _[/FONT]

------

I've tried typing help for a list of built in commands, but that didn't seem to help.

What should I do?

---

### Post by Alternative Solution on 2010-11-04
When you answer, please let me know how this could have happened, and how to fix it.

---

### Post by P4man on 2010-11-05
Would be helpful if we knew what version of ubuntu you were using, and if you upgraded to a new release, or just updated the system. Anyway, same issue reported here:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10072707](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10072707)

I suggest you follow the same advice posted there.

BTW, that uuid isnt a security risk. Its just a number identifying your drive. We cant do anything with it ;)

---

