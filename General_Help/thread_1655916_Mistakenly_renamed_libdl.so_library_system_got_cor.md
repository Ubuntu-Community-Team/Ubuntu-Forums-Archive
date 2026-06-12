---
title: "Mistakenly renamed libdl.so library: system got corrupted"
date: 2010-12-30
forum: General Help
---

### Post by royalibrahim on 2010-12-30
Hi,

I am using [COLOR=DarkRed]_Ubuntu 8.04 64-bit _[/COLOR](Hardy Heron LTS Desktop edition) OS on a 64-bit intel hardware (x86_64). I have wrongly renamed the **/lib64/libdl-2.7.so** shared library file and now hardly few commands are working. My Gnome UI display has gone and I could not establish any new connection via SSH. I cannot run "ls" or "mv", or "cp" as these basic commands rely on libdl library for dlopen, dlclose operations etc,. It is a build server machine for our project and I am reluctant to reboot the system as it has to be run 24/7 (Hudson setup is there).

How I can resolve the system now? I guess recovery mode does not help in this case.
What if I boot via Ubuntu installation Live CD and mount the hard-disk and do the rename? Will it help?

What other options I have been left out?

This is really an urgent issue. Your help is highly solicited and appreciated.

---

### Post by hawkmage on 2010-12-30
Booting from the Live CD, mounting the volume and renaming the file back is what I was going to recommend.  That was a really bad lib to rename, it is used by any program that dynamically loads a library.

---

### Post by drpjkurian on 2010-12-30
yep rename it with live cd, it should work. If you wish to do a backup of everything with live cd, you can try my [blog]("http://http://ubuntucrack.blogspot.com/2010/12/backup-your-system-by-using-ubuntu-live.html")

---

