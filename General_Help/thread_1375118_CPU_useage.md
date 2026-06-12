---
title: "CPU useage"
date: 2010-01-07
forum: General Help
---

### Post by Robbyx on 2010-01-07
I am in Karmic. Htop shows two programs taking up almost 100% of both cores:

mixer_applet2 
*After some searches I decided to  kill the applet via htop, but is there a more permanent solution? I use a timed sleep setting on my machine and it may be connected to the problem from what I read. *

google/desktop/ gdl_indexer
[I]When I load the quick search box of google desktop I can not open the google indexer settings. This is what appears in the url but it does not open in the browser:
[http://127.0.0.1:30073/options?hl=en_GB&src=14&s=eW_2L711vY7h5M6VIJMAimpx27c](http://127.0.0.1:30073/options?hl=en_GB&src=14&s=eW_2L711vY7h5M6VIJMAimpx27c)[/I]


Is there anything I should and could do to reduce their appetites? The machine is running slowly because of them.

---

### Post by Robbyx on 2010-01-08
Could I please have a reply, particularly to the google index problem.

---

### Post by OllyDBG on 2010-01-08
u tried "renice" command?

```
renice <priority> <PID>
```<priority> = say give it 10, PID is the ID of the process

```
renice 10 <PID>
```

---

### Post by Robbyx on 2010-01-08
Thank you for your suggestion. I have applied it. Any ideas about the failure to access the google search preferences? I have reinstalled the desktop search and it has made no difference.

---

