---
title: "How to improve a bug report for dbus daemon?"
date: 2011-10-06
forum: General Help
---

### Post by SeanTater on 2011-10-06
Hello everyone!
 I'm having an issue with dbus-daemon using 100% cpu and I'd like to know if there's a way that I can generate good bug reports without needing to start graphical programs via graphical means. (e.g. I might be able to start it with a command but the run dialogs and such are frozen.)

I've run strace:
```

sudo strace -p 2109
.... several thousand lines in about a second
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=6, events=POLLIN}, {fd=8, events=POLLIN}, {fd=9, events=POLLIN}, {fd=11, events=POLLIN}, {fd=13, events=POLLIN}, {fd=14, events=POLLIN}, {fd=15, events=POLLIN}, {fd=16, events=POLLIN}, {fd=17, events=POLLIN}, {fd=18, events=POLLIN}, {fd=21, events=POLLIN}, {fd=20, events=POLLIN}, {fd=19, events=POLLIN}, {fd=22, events=POLLIN}, {fd=24, events=POLLIN}, {fd=26, events=POLLIN}, {fd=27, events=POLLIN}, {fd=25, events=POLLIN}, {fd=30, events=POLLIN}, {fd=31, events=POLLIN}, {fd=32, events=POLLIN}, {fd=33, events=POLLIN}, {fd=34, events=POLLIN}, {fd=35, events=POLLIN}, {fd=36, events=POLLIN}, {fd=37, events=POLLIN}, {fd=38, events=POLLIN}, {fd=39, events=POLLIN}, {fd=40, events=POLLIN}, {fd=41, events=POLLIN}, ...], 1018, -1) = 1 ([{fd=3, revents=POLLIN}])
accept4(3, 0x7fffa04c38b0, [16], SOCK_CLOEXEC) = -1 EMFILE (Too many open files)
fcntl(-1, F_GETFD)                      = -1 EBADF (Bad file descriptor)
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=6, events=POLLIN}, {fd=8, events=POLLIN}, {fd=9, events=POLLIN}, {fd=11, events=POLLIN}, {fd=13, events=POLLIN}, {fd=14, events=POLLIN}, {fd=15, events=POLLIN}, {fd=16, events=POLLIN}, {fd=17, events=POLLIN}, {fd=18, events=POLLIN}, {fd=21, events=POLLIN}, {fd=20, events=POLLIN}, {fd=19, events=POLLIN}, {fd=22, events=POLLIN}, {fd=24, events=POLLIN}, {fd=26, events=POLLIN}, {fd=27, events=POLLIN}, {fd=25, events=POLLIN}, {fd=30, events=POLLIN}, {fd=31, events=POLLIN}, {fd=32, events=POLLIN}, {fd=33, events=POLLIN}, {fd=34, events=POLLIN}, {fd=35, events=POLLIN}, {fd=36, events=POLLIN}, {fd=37, events=POLLIN}, {fd=38, events=POLLIN}, {fd=39, events=POLLIN}, {fd=40, events=POLLIN}, {fd=41, events=POLLIN}, ...], 1018, -1) = 1 ([{fd=3, revents=POLLIN}])
accept4(3, 0x7fffa04c38b0, [16], SOCK_CLOEXEC) = -1 EMFILE (Too many open files)
fcntl(-1, F_GETFD)                      = -1 EBADF (Bad file descriptor)
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=6, events=POLLIN}, {fd=8, events=POLLIN}, {fd=9, events=POLLIN}, {fd=11, events=POLLIN}, {fd=13, events=POLLIN}, {fd=14, events=POLLIN}, {fd=15, events=POLLIN}, {fd=16, events=POLLIN}, {fd=17, events=POLLIN}, {fd=18, events=POLLIN}, {fd=21, events=POLLIN}, {fd=20, events=POLLIN}, {fd=19, events=POLLIN}, {fd=22, events=POLLIN}, {fd=24, events=POLLIN}, {fd=26, events=POLLIN}, {fd=27, events=POLLIN}, {fd=25, events=POLLIN}, {fd=30, events=POLLIN}, {fd=31, events=POLLIN}, {fd=32, events=POLLIN}, {fd=33, events=POLLIN}, {fd=34, events=POLLIN}, {fd=35, events=POLLIN}, {fd=36, events=POLLIN}, {fd=37, events=POLLIN}, {fd=38, events=POLLIN}, {fd=39, events=POLLIN}, {fd=40, events=POLLIN}, {fd=41, events=POLLIN}, ...], 1018, -1) = 1 ([{fd=3, revents=POLLIN}])
accept4(3, 0x7fffa04c38b0, [16], SOCK_CLOEXEC) = -1 EMFILE (Too many open files)
fcntl(-1, F_GETFD)                      = -1 EBADF (Bad file descriptor)
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=6, events=POLLIN}, {fd=8, events=POLLIN}, {fd=9, events=POLLIN}, {fd=11, events=POLLIN}, {fd=13, events=POLLIN}, {fd=14, events=POLLIN}, {fd=15, events=POLLIN}, {fd=16, events=POLLIN}, {fd=17, events=POLLIN}, {fd=18, events=POLLIN}, {fd=21, events=POLLIN}, {fd=20, events=POLLIN}, {fd=19, events=POLLIN}, {fd=22, events=POLLIN}, {fd=24, events=POLLIN}, {fd=26, events=POLLIN}, {fd=27, events=POLLIN}, {fd=25, events=POLLIN}, {fd=30, events=POLLIN}, {fd=31, events=POLLIN}, {fd=32, events=POLLIN}, {fd=33, events=POLLIN}, {fd=34, events=POLLIN}, {fd=35, events=POLLIN}, {fd=36, events=POLLIN}, {fd=37, events=POLLIN}, {fd=38, events=POLLIN}, {fd=39, events=POLLIN}, {fd=40, events=POLLIN}, {fd=41, events=POLLIN}, ...], 1018, -1) = 1 ([{fd=3, revents=POLLIN}])
accept4(3, 0x7fffa04c38b0, [16], SOCK_CLOEXEC) = -1 EMFILE (Too many open files)
fcntl(-1, F_GETFD)                      = -1 EBADF (Bad file descriptor)
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=6, events=POLLIN}, {fd=8, events=POLLIN}, {fd=9, events=POLLIN}, {fd=11, events=POLLIN}, {fd=13, events=POLLIN}, {fd=14, events=POLLIN}, {fd=15, events=POLLIN}, {fd=16, events=POLLIN}, {fd=17, events=POLLIN}, {fd=18, events=POLLIN}, {fd=21, events=POLLIN}, {fd=20, events=POLLIN}, {fd=19, events=POLLIN}, {fd=22, events=POLLIN}, {fd=24, events=POLLIN}, {fd=26, events=POLLIN}, {fd=27, events=POLLIN}, {fd=25, events=POLLIN}, {fd=30, events=POLLIN}, {fd=31, events=POLLIN}, {fd=32, events=POLLIN}, {fd=33, events=POLLIN}, {fd=34, events=POLLIN}, {fd=35, events=POLLIN}, {fd=36, events=POLLIN}, {fd=37, events=POLLIN}, {fd=38, events=POLLIN}, {fd=39, events=POLLIN}, {fd=40, events=POLLIN}, {fd=41, events=POLLIN}, ...], 1018, -1) = 1 ([{fd=3, revents=POLLIN}])
accept4(3, 0x7fffa04c38b0, [16], SOCK_CLOEXEC) = -1 EMFILE (Too many open files)
fcntl(-1, F_GETFD)                      = -1 EBADF (Bad file descriptor)
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=6, events=POLLIN}, {fd=8, events=POLLIN}, {fd=9, events=POLLIN}, {fd=11, events=POLLIN}, {fd=13, events=POLLIN}, {fd=14, events=POLLIN}, {fd=15, events=POLLIN}, {fd=16, events=POLLIN}, {fd=17, events=POLLIN}, {fd=18, events=POLLIN}, {fd=21, events=POLLIN}, {fd=20, events=POLLIN}, {fd=19, events=POLLIN}, {fd=22, events=POLLIN}, {fd=24, events=POLLIN}, {fd=26, events=POLLIN}, {fd=27, events=POLLIN}, {fd=25, events=POLLIN}, {fd=30, events=POLLIN}, {fd=31, events=POLLIN}, {fd=32, events=POLLIN}, {fd=33, events=POLLIN}, {fd=34, events=POLLIN}, {fd=35, events=POLLIN}, {fd=36, events=POLLIN}, {fd=37, events=POLLIN}, {fd=38, events=POLLIN}, {fd=39, events=POLLIN}, {fd=40, events=POLLIN}, {fd=41, events=POLLIN}, ...], 1018, -1) = 1 ([{fd=3, revents=POLLIN}])
... It keeps going..

```

... but I think that report would probably be pretty vague. Is there something else I could run (maybe something else I need to install?) in order to make a more useful report?

---

### Post by SeanTater on 2011-10-06
ah ha.. It turns out that the reason it had too many open files was on account of kpackagekitsmarticon.
I ran 
```
sudo mv /usr/lib/kde4/libexec/kpackagekitsmarticon  /usr/lib/kde4/libexec/kpackagekitsmarticon_; killall kpackagekitsmarticon
``` in order to simply destroy the icon. Now it's not a problem. There's already a bug report on it and it's been fixed: [https://bugs.kde.org/show_bug.cgi?id=261180](https://bugs.kde.org/show_bug.cgi?id=261180)

---

