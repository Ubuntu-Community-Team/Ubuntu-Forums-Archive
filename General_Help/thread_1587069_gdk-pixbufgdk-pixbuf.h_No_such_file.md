---
title: "gdk-pixbuf/gdk-pixbuf.h: No such file"
date: 2010-10-02
forum: General Help
---

### Post by mjsilverstri on 2010-10-02
Hi,

I have updated to ubuntu 10.10, but when I try to compile chromium on ubuntu, I get this error:

```
In file included from /usr/include/gtk-2.0/gdk/gdkcairo.h:28,
                 from /usr/include/gtk-2.0/gdk/gdk.h:33,
                 from app/active_window_watcher_x.cc:6:
/usr/include/gtk-2.0/gdk/gdkpixbuf.h:37: fatal error: gdk-pixbuf/gdk-pixbuf.h: No such file or directory

```

What I don't understand is why gtk-2.0/gdk/gdkpixbuf.h complains that gdkpixbuf/gdk-pixbuf.h is not found. And how can I fix it?

Thank you.

---

### Post by mc4man on 2010-10-02
Do you have libgdk-pixbuf2.0-dev installed?

---

### Post by mjsilverstri on 2010-10-03
Yes, I did have libgdk-pixbuf2.0-dev installed. I still have that problem.

---

### Post by mc4man on 2010-10-03
Can you post a link to the source you're using?

---

### Post by mjsilverstri on 2010-10-03
[http://code.google.com/p/chromium/wiki/UsingGit](http://code.google.com/p/chromium/wiki/UsingGit)

---

### Post by mc4man on 2010-10-03
I guess you may wish to explain what your goal is here and provide a bit more info on your method of building.

Went ahead and did a build of 7.0.543.0 (61336), outed as Release w/ all tests (and there are **alot** of tests

The only issue was w/ src/breakpad/src/tools/linux/md2core/minidump-2-core.cpp, but adding a couple of #includes resolved that

I didn't see any issue as far as gdk-pixbuf.h:, actually not even sure it's a dep. (libgtk2.0-dev is.

The difference between lucid and maverick is libgdk-pixbuf2.0 is now a separate package rather than a part of libgtk2.0, but again don't see any issue

(if you simply just want the latest chrome (chromium) browser than why not use the daily ppa?

---

### Post by l0xin on 2010-11-13
Same issue trying to install [VEDICS](https://sourceforge.net/projects/vedics/)

I started amending the paths in the header files to the correct locations, but gave up after  fixing around 15.

---

### Post by piponazo on 2010-11-18
Same problem!
I'm starting with gtk/gdk programming and simply including the header <gtk/gtk.h> this error is raised >_<.

I also have Ubuntu 10.10.

---

