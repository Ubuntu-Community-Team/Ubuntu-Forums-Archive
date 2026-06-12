---
title: "External HD being accessed 1x per hour"
date: 2009-11-13
forum: General Help
---

### Post by BobvanderPoel on 2009-11-13
I've got an external USB hard drive which gets mounted on boot. It's entry in /etc/fstab is:

UUID=8dca643b-5736-4dab-a93e-e9a448966735 /media/external1 auto user,atime,auto,rw,nodev,noexec,nosuid 2 2

I use this for a backup drive. The only access (unless I need to restore something) is via backintime which does its magic at midnight every day.

Works just fine. But, I notice that about 1x per hour the HD light flashes and the drive spins up (well, I think that is what is happening). In previous installs (8.04) the drive just sat there in sleep mode until needed. Now, it seems that it's getting started up frequently. Not that I'm concerned about it wearing out (but that might be a concern).

I just find the click-click-whirl sound annoying. Plus, I'm curious as to what is accessing the drive.

So, 2 questions:

1. How to figure out what is causing the access.

2. Can I disable whatever is running in (1)? safely?

Thanks.

---

