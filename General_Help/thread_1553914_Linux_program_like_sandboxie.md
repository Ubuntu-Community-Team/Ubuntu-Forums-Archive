---
title: "Linux program like sandboxie?"
date: 2010-08-15
forum: General Help
---

### Post by wakkawakka on 2010-08-15
Hey all.  

This isn't an Ubuntu-specific question, so I apologize for posting it here.  

If my post isn't appropriate for this forum/subsection, please feel free to remove it. 

I've been wanting to switch to Linux for a long time now.

However, there's a Windows program that I'm so dependent on that I don't know if I can make the switch without finding a reasonable replacement for it under Linux.  

The program is called Sandboxie ([www.sandboxie.com]("http://www.sandboxie.com")).  

For those who aren't familiar, Sandboxie allows you to run programs in such a way that they're (somewhat) isolated from the rest of the operating system, and make no permanent changes to data on the hard drive.  

I've spent a few hours looking for how to get similar functionality under Linux, and it doesn't seem to exist. 

I've read a bit about chroot and jails and such - and I'm sure some of this is owing to my sheer lack of experience with linux - but nothing I've read about seems like it can do what Sandboxie does.

Everything I've read about that currently exists under Linux seems more geared toward keeping process a from sharing info with process b - and that's great and all - but I'm looking for something that will run process b with only read permissions for anything that it wants to access outside of it's own sandbox/jail/whatever.

At least, not without hand-tweaking something from the command line for each application you'd like to run in this way.

And right now, with as little experience with Linux as I have, that would be beyond my ability/time/energy to do.  

I know I can install XP in a virtual machine and run that inside Linux, but in most cases, that just wouldn't be practical.  

So if you know of any way I can do under Linux what Sandboxie does under windows (that a real, total novice can do), I'd love to hear from you.  

Thanks for your help in advance.  

And once again, if this post isn't right for this forum, don't be afraid to move or kill it.  No offense, promise.

---

### Post by deserthowler on 2010-08-15
Most of the people I know interested in security run Linux with Firefox.  They install add-ons for security.

I have the following installed on my computer:
AdblockPlus
BeefTaco
BetterPrivacy
Ghostery
GoogleSharing
NoScript

I'm sure others can be added to this list.

Earl

---

### Post by Rubi1200 on 2010-08-15
Hi wakkawakka,
this doesn't exactly answer your question, but I thought you might find it interesting:

[http://en.wikipedia.org/wiki/Role-based_access_control](http://en.wikipedia.org/wiki/Role-based_access_control)

---

### Post by bodhi.zazen on 2010-08-15
I think either selinux or apparmor are the closest to what you want.

Here is one example :

[http://danwalsh.livejournal.com/28545.html](http://danwalsh.livejournal.com/28545.html)

Although you may want virtualization - chroot, openvz, or Linux containers, depending on what you want to use such a sandbox for exactly.

---

