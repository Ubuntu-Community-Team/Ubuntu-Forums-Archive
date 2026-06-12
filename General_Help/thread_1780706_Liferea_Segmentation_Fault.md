---
title: "Liferea Segmentation Fault"
date: 2011-06-12
forum: General Help
---

### Post by isecore on 2011-06-12
Anyone else having problems with Liferea? This started happening today. It doesn't start at all. When I ran it in a terminal it spits out a bunch of messages and then finally it does this:

```
(liferea:13349): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed
Segmentation fault
```

So, anyone have a clue?

I filed a bug-report here in case anyone is interested: [https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/796234](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/796234)

---

### Post by Yellow Pasque on 2011-06-12
I can't reproduce the issue on my Natty VM. For your bug report, you'll need to obtain a backtrace before a dev will look at the issue.
```
sudo apt-get install liferea-dbg gdb
```
Now, follow this to get the backtrace: [https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)

---

### Post by isecore on 2011-06-12
Done and done. Hope it helps to whoever is the responsible party.

---

### Post by isecore on 2011-06-22
If it's of any use, it runs fine when run as root using sudo.

---

### Post by WegDamit on 2011-06-26
+1

---

### Post by isecore on 2011-06-26
I managed to get it sorted, although I'm very fuzzy about what I did. I also got that GDK_IS_PIXBUF error as the final message before the segfault.

In my case, I noticed that it ran fine as root (sudo liferea) and after that I discovered that it ran fine if I created a fresh user and logged in there. So I went through all the files in ~ and deleted everything that looked old or irrelevant. Somewhere along this it got fixed. I have NO IDEA what I changed but it works again.

---

