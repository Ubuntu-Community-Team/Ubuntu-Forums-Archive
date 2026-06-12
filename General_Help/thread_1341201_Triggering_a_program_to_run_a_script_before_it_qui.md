---
title: "Triggering a program to run a script before it quits?"
date: 2009-11-29
forum: General Help
---

### Post by lemuriens on 2009-11-29
Hi,

I just followed the HOWTO on this arch linux wiki page:

[http://wiki.archlinux.org/index.php/Speed-up_Firefox_using_tmpfs](http://wiki.archlinux.org/index.php/Speed-up_Firefox_using_tmpfs)

In short, the active firefox profile is on tmpfs to make firefox more responsive (it works incredibly with my acer aspire one :D). I've set cron to run the script to write the active firefox profile to the standard profile directory every hour, and it's also loaded/saved when the computer starts up and shuts down respectively.

The only problem is that the page doesn't cover how to write the active tmpfs profile to the disk drive when firefox closes. As a result, I lose all my browsing history from the however many minutes firefox has been running since the last write.

Does anyone have any suggestions on how I can make the profile-saving script run when I close firefox, or is this something I'll just have to put up with?

---

