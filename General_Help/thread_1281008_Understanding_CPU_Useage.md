---
title: "Understanding CPU Useage"
date: 2009-10-02
forum: General Help
---

### Post by MaaaTtY on 2009-10-02
Hey im brandnew to Ubuntu and Linux in general very happy so far but i just have some questions about my CPU Useage.

i noticed a few things, first of all when i open system monitor some of the cores will be running at say 40% and others will be at 0%.  is this how it usually works? it seems more often than not only 1 core will be working at a time.

[http://img22.imageshack.us/img22/9732/screenshottrs.png](http://img22.imageshack.us/img22/9732/screenshottrs.png)

My other question is when my CPU is under a fair amount of load and i open system monitor and sort by CPU usage there is almost never anything listed as using more than 1-3%.  even though the CPU monitor in my panel shows constant activity.

... im just use to windows, trying to understand how stuff works.  im use to all my cores using roughly the same CPU % and working together and when im having problems with a program i check the process list and can see exactly which ones are using up all my CPU.

---

### Post by XCan on 2009-10-02
I think the issue is that the gnome-system-monitor is a huge resource hog. It easily maxes out one core on my overclocked Q9450. If you want to check for the usage, you should at this time probably use top in a terminal.

---

### Post by MaaaTtY on 2009-10-02
oh nice, thats better.

---

### Post by jward3010 on 2009-10-02
Here's a command you should use - "top".
Open a terminal and type that. It lists the top running processes, there memory usage etc. etc. Not anywhere as heavy as system-monitor.

---

