---
title: "Programs use all cpu, and won't work"
date: 2010-07-12
forum: General Help
---

### Post by NoBugs! on 2010-07-12
Trying to start a new program results in a blank window with the name of the program, but nothing else. For example: strace wxmaxima gives:

```
...

gettimeofday({1278955762, 968311}, NULL) = 0
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN}, {fd=14, events=POLLIN}, {fd=15, events=POLLOUT}, {fd=18, events=POLLIN}], 9, 0) = 1 ([{fd=12, revents=POLLHUP}])
read(5, 0x8dbc4a0, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1278955762, 968453}, NULL) = 0
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN}, {fd=14, events=POLLIN}, {fd=15, events=POLLOUT}, {fd=18, events=POLLIN}], 9, 0) = 1 ([{fd=12, revents=POLLHUP}])
read(5, 0x8dbc4a0, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1278955762, 982719}, NULL) = 0
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN}, {fd=14, events=POLLIN}, {fd=15, events=POLLOUT}, {fd=18, events=POLLIN}], 9, 0) = 1 ([{fd=12, revents=POLLHUP}])
read(5, 0x8dbc4a0, 4096)                = -1 EAGAIN (Resource temporarily unavailable)

```
The Resource temporarily unavailable keeps repeating and it uses all cpu. Same error happens with any program. Amarok says "The process for the file protocol died unexpectedly."

---

### Post by dragos240 on 2010-07-12
Has it been doing this? Or is it just doing it now, if it's the latter, reboot. If that doesn't work, open a program in the terminal, and when it fails, post this:
dmesg

---

### Post by NoBugs! on 2010-07-12
I also noticed "read-only filesystem" error before shut down.
After reboot and a disk-check, it said there were errors on /. After it fixed them, it works fine again. Looks like some program somehow messed up the file system? I had this same exact problem awhile ago, is there any way to keep this from happening?

---

### Post by NoBugs! on 2010-07-12
All the tests in GSmartControl give "Test result: Completed without error", so it must be a software problem? a bug in the kernel?

---

### Post by NoBugs! on 2010-10-27
I'm noticing a similar problem again... When selecting the "Open" button in a gtk based program, it crashes. Apport crash reporter shows "Title: programname crashed with SIGSEGV in g_cclosure_marshal_VOID__VOID()" and "SegvReason: writing unknown VMA", in every crash. Other programs that don't use the standard open dialog don't have this problem.

---

### Post by NoBugs! on 2011-01-12
I'm getting a similar error again... I can't save file in home or /tmp, it always says "read only file system". Could this have something to do with Virtualbox running recently? Is there some way to make filesystem read-write again?

---

### Post by no2498 on 2011-01-12
install htop type it in a terminal it tells you how to install it
after installed type htop click enter
see what is hitting the cpu so hard
you can kill/stop it
it gives you something to work with
or what needs fixed

---

