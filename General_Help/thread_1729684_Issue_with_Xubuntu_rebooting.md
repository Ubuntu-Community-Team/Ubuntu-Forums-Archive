---
title: "Issue with Xubuntu rebooting"
date: 2011-04-15
forum: General Help
---

### Post by rwb7041 on 2011-04-15
I am having an issue with rebooting my Xubuntu system. When I ssh in and send a "sudo reboot" command, it appears to start rebooting properly. But then I go and look at the desktop and the last thing it says is that the system is now rebooting, but it never gets anywhere. I tried to look around to find a solution to this problem but haven't found any. Anyone have any ideas what the problem could be?

thanks,
rwb7041

---

### Post by ghostborg on 2011-04-15
Try adding an option maybe it's waiting for something.
shutdown --help
reboot --help

I did notice this comment in the reboot help text:

This command is intended to instruct the kernel to reboot or halt the system; when run without the -f option, or when in a system
runlevel other than 0 or 6, it will actually execute /sbin/shutdown.

try sudo shutdown -r 0

---

