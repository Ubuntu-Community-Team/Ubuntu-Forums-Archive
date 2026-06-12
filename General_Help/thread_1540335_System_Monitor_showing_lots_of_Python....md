---
title: "System Monitor showing lots of Python..."
date: 2010-07-27
forum: General Help
---

### Post by Cybrmerc on 2010-07-27
My system monitor is showing lots of Python. When I was on windows, I was always worried about a bulky processes list, so I was wondering if this should be considered in Ubuntu. Each of the python processes is using around 24 MB of memory. I am running several screenlets, but not as many as I see in the sysmon. I just don't want a memory hole due to startup processes I don't need.

[IMG]http://img826.imageshack.us/img826/3122/sysmonpython.png[/IMG]

---

### Post by dmaxel on 2010-11-30
I actually have a similar problem as well, but I don't know what's causing it either. I used to run screenlets, but I turned them off a long while ago, and I still have a lot of python processes.

EDIT: Nevermind, I found a way to figure out what's going on. If you hover over each process (if nothing appears, you might need to hover for a second or two, then move your mouse to the left or right, staying on the same line/process, then stopping again), you can see the path of what each process is. For me, I had too many Docky helpers running. So I went through my list again and deactivated any that I pretty much didn't use, use too rarely, or have other ways of doing things that the helpers do.

---

