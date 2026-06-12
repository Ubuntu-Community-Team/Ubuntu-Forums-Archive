---
title: "ubuntu not booting"
date: 2011-06-24
forum: General Help
---

### Post by npsabari on 2011-06-24
I installed Ubuntu 11.04 a month ago. Everything was working fine till yesterday. Today when I booted ubuntu in normal mode, it displayed lot of starting.. stopping... statements and it got struck at "Starting userspace bootsplash".
When I tried to open in recovery mode-->failsafex mode, it's booting properly(without prompting password!!) and everything is working fine..
But it's not booting in normal mode..!! and gets struck at a different "starting......." statement this time..
Please Help regarding logging in normal mode..

My PC details : Dell XPS,Intel i5 processor, 1Gb graphics card..

---

### Post by dino99 on 2011-06-24
at first glance i'll try without splash (edit the boot line to remove it)

then logs might help you find whats wrong:
- .xsession-errors (/home, ctrl+h to unhide it)
- /var/log/ (system admin logviewer)

---

### Post by yotam on 2011-06-24
If system partitions have bad file-system state
you may try booting Live-CD and try fixing the manually
via appropriate **fsck** variant and parameters.

---

