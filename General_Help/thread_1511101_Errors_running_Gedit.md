---
title: "Errors running Gedit"
date: 2010-06-16
forum: General Help
---

### Post by yeleek on 2010-06-16
Hi,

Had no problems running Gedit, I often run from a terminal and get no errors.

Just - about 5 mins ago - install conky-all and curl from the repositories.

Now when starting gedit from terminal get this

```
ben@WOPR:~$ gedit

** (gedit:4878): CRITICAL **: cr_parser_new_from_buf: assertion `a_buf && a_len' failed

** (gedit:4878): CRITICAL **: cr_parser_set_sac_handler: assertion `a_this' failed

(gedit:4878): librsvg-WARNING **: Error setting CSS SAC handler


** (gedit:4878): CRITICAL **: cr_parser_destroy: assertion `a_this && PRIVATE (a_this)' failed
```


Any ideas please?

---

### Post by dino99 on 2010-06-16
either conky or curl have problem: check the packages releases with their dependencies (look at details), be sure you dont mixed releases into sources.list, maybe clean the cache

you can remove/purge then reinstall the packages

---

### Post by yeleek on 2010-06-16
Thanks for reply

Curl libc6 >=2.7

Conky depends on libc6 >=2.9

I'm running lucid and have 2.11

That is the only shared item.

Conky does add depend on libcurl3-gnutils >=7.16.2-1 and curl depends on libcurl3 >=7.16.2-1.

Tried removing curl/conky-all then cleaning no joy

Any ideas pls?

---

### Post by yeleek on 2010-06-17
Anyone have any ideas pls?

---

### Post by yeleek on 2010-06-18
Last try - anyone else pls?

---

### Post by 3rdalbum on 2010-06-18
> **yeleek said:**
> Last try - anyone else pls?

Gnome   programs   sometimes   print   error   messages   to   the   terminal   even   when   they   are   working   fine.   Is  Gedit   working?   If   so,   then   the   messages   are   nothing  to   worry   about.

---

