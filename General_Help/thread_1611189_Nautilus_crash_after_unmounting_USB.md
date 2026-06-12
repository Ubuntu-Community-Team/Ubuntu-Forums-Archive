---
title: "Nautilus crash after unmounting USB"
date: 2010-11-01
forum: General Help
---

### Post by lazylew on 2010-11-01
10.10 MMeerkat - When I use a USB-stick or external hard drive, I don't get the "unmount" option but instead it says "safely remove drive".
When I click this, Nautilus immediately crashes and is gone.

Is this a known bug in 10.10?

---

### Post by Viva on 2010-11-22
I have the same problem.

---

### Post by wyth on 2010-12-05
It looks like [a bug was filed for this very problem way back in Karmic]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/462364"). It persisted at least through Lucid. 

It looks like as with many other bugs, the fix was to ask if upgrading helped, and there was no further response. There was also [this bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/514437") (again 9.10), which was immediately closed when the answer was to turn on apport in order to get more info.

I wonder if it's worth jumping back on that first report, or if a new bug is in order, or if filing a new bug will just get relegated to duplicate status.

---

### Post by rogerdean on 2010-12-06
I've got it here too. I don't remember it as an issue in Lucid, but happens on 50% of usb removals for me

---

### Post by fizzyh2o on 2011-01-24
I'm on 10.10 and the same happens for me.  I can't find any correlation between Nautilus crashing and anything else going on.  Every time I "safely remove remove" my drive I find my self playing gambling that I wont loose all my tabs.

Here's the error message I'm getting in syslog

Jan 25 00:53:52 fizzyh2o kernel: [37331.152099] nautilus[1809]: segfault at 1 ip 0808fb0c sp bfc00fd0 error 4 in nautilus[8048000+1af000]

Anyone have any ideas?

---

### Post by robroyality on 2011-01-25
I'm on Ubuntu 10.10 (x64_64) too. It doesn't matter if I umount the USB-disks/sticks manually (f.e.: umount /media/UE320) or if I'm using the nautilus-way all my nautilus-sessions are crashing as soon as I'm umounting USB-drives.

Here some strace-output from the last (reproduceable) crash:
> ...
mmap(NULL, 280, PROT_READ, MAP_SHARED, 51, 0) = 0x7ff4811fb000
open("/home/{*username*}/.local/share/gvfs-metadata/computer:-663b2f44.log", O_RDONLY) = 52
fstat(52, {st_mode=S_IFREG|0644, st_size=32768, ...}) = 0
mmap(NULL, 32768, PROT_READ, MAP_SHARED, 52, 0) = 0x7ff4811f3000
read(3, 0x13fe424, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=6, events=POLLIN}, {fd=13, events=POLLIN}, {fd=19, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN|POLLPRI}, {fd=20, events=POLLIN|POLLPRI}, {fd=21, events=POLLIN|POLLPRI}, {fd=39, events=POLLIN}, {fd=40, events=POLLIN}, {fd=24, events=POLLIN}, {fd=33, events=POLLIN}, {fd=26, events=POLLIN}, {fd=25, events=POLLIN}, {fd=49, events=POLLIN}, {fd=50, events=POLLIN}], 16, 0) = 0 (Timeout)
read(3, 0x13fe424, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=6, events=POLLIN}, {fd=13, events=POLLIN}, {fd=19, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN|POLLPRI}, {fd=20, events=POLLIN|POLLPRI}, {fd=21, events=POLLIN|POLLPRI}, {fd=39, events=POLLIN}, {fd=40, events=POLLIN}, {fd=24, events=POLLIN}, {fd=33, events=POLLIN}, {fd=26, events=POLLIN}, {fd=25, events=POLLIN}, {fd=49, events=POLLIN}, {fd=50, events=POLLIN}], 16, 0) = 0 (Timeout)
stat("sys", 0x7fffc3c17f80)             = -1 ENOENT (No such file or directory)
stat("/usr/lib/nautilus/extensions-2.0/python/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/nautilus/extensions-2.0/python/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/nautilus/extensions-2.0/python/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/nautilus/extensions-2.0/python/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/nautilus-python/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/plat-linux2/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/lib-tk/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/lib-old/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/lib-dynload/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/python2.6/dist-packages/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/dist-packages/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/dist-packages/PIL/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/dist-packages/gst-0.10/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/pymodules/python2.6/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/dist-packages/gtk-2.0/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/pymodules/python2.6/gtk-2.0/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/sys", 0x7fffc3c17f80) = -1 ENOENT (No such file or directory)
stat("/usr/share/sys", 0x7fffc3c17f80)  = -1 ENOENT (No such file or directory)
stat("/usr/share/sys", 0x7fffc3c17f80)  = -1 ENOENT (No such file or directory)
write(2, "sys:1: Warning: g_object_get_qda"..., 76) = 76
stat("sys", 0x7fffc3c17fc0)             = -1 ENOENT (No such file or directory)
stat("/usr/lib/nautilus/extensions-2.0/python/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/nautilus/extensions-2.0/python/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/nautilus/extensions-2.0/python/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/nautilus/extensions-2.0/python/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/nautilus-python/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/plat-linux2/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/lib-tk/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/lib-old/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/lib-dynload/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/python2.6/dist-packages/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/dist-packages/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/dist-packages/PIL/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/dist-packages/gst-0.10/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/pymodules/python2.6/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/dist-packages/gtk-2.0/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/pymodules/python2.6/gtk-2.0/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/sys", 0x7fffc3c17fc0) = -1 ENOENT (No such file or directory)
stat("/usr/share/sys", 0x7fffc3c17fc0)  = -1 ENOENT (No such file or directory)
stat("/usr/share/sys", 0x7fffc3c17fc0)  = -1 ENOENT (No such file or directory)
write(2, "sys:1: GtkWarning: IA__gtk_widge"..., 95) = 95
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
Process 9470 detached
According to this [article]("http://forums.fedoraforum.org/archive/index.php/t-256368.html") it could also be a pure nautilus-problem that should be solved in version 2.32.2 (right now 10.10 seems to use 2.32.0).

KR

---

