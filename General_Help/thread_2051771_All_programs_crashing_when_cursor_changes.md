---
title: "All programs crashing when cursor changes"
date: 2012-09-02
forum: General Help
---

### Post by euphgeek on 2012-09-02
Ubuntu 12.04 Precise Pangolin, 64-bit version

I've been looking for a solution to this problem for months.  Basically, what happens is any time I do something in a program like drag and drop in Nautilus or if I try to magnify an image in Firefox, the program crashes.  I've notice this happens whenever the cursor changes to the magnifying glass, the circle with a slash through it or the copy wedge.  It also happens when I try to type something into a dialog box, for example typing the number of pages to print.  Can anyone help me?  If this is a known issue, could someone link me to the solution?

---

### Post by 2F4U on 2012-09-02
I don't think this is a common problem, at least I haven't read before about it here on the forums. Can you post your hardware specs and what graphics driver you are using? Did you look into the system log file whether there is any hint on the problem?

---

### Post by euphgeek on 2012-09-02
I don't think it's a hardware problem, since I've been using the same hardware all along and this is a more recent issue, but I'm using the fglrx driver for my onboard graphics card.  I've also tried the ati driver and it does the same thing.

Here's a couple of errors from /var/log/syslog:

```
Sep  2 11:20:32 localhost kernel: [492264.856570] nautilus[10273]: segfault at 7fffa1b0afe8 ip 00007f1ff6108045 sp 00007fffa1b0aff0 error 6 in libc-2.15.so[7f1ff609a000+1b3000]
Sep  2 11:21:27 localhost kernel: [492319.621669] nautilus[11039]: segfault at 7fff74d04fc8 ip 00007fee7b8c9045 sp 00007fff74d04fd0 error 6 in libc-2.15.so[7fee7b85b000+1b3000]
Sep  2 11:21:44 localhost gnome-session[10934]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
```Here's some from /var/log/kern.log:

```
Sep  2 11:20:32 localhost kernel: [492264.856570] nautilus[10273]: segfault at 7fffa1b0afe8 ip 00007f1ff6108045 sp 00007fffa1b0aff0 error 6 in libc-2.15.so[7f1ff609a000+1b3000]
Sep  2 11:21:27 localhost kernel: [492319.621669] nautilus[11039]: segfault at 7fff74d04fc8 ip 00007fee7b8c9045 sp 00007fff74d04fd0 error 6 in libc-2.15.so[7fee7b85b000+1b3000]
Sep  2 11:24:02 localhost kernel: [492475.081598] gksu[12297]: segfault at 7fffb6869fe8 ip 00007f7fe7e0e045 sp 00007fffb6869ff0 error 6 in libc-2.15.so[7f7fe7da0000+1b3000]
```

---

### Post by euphgeek on 2012-09-16
I figured it out.  It was the cursor theme that was causing it to crash.

---

