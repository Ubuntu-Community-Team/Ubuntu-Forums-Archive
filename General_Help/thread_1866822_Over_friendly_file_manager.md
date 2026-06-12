---
title: "Over friendly file manager"
date: 2011-10-22
forum: General Help
---

### Post by niranjan_rao on 2011-10-22
I have a shell script that uses truecrypt to mount the file as truecrypt volume, apply changes to newly mounted device and unmount. This process is repeated for many files in a loop.

My script does work fine, but the problem with 11.10 is every time I mount a truecrypt volume, nautilus opens, grabs focus, and starts showing the new mounted device. 

This is very useful for normal mount operations however very painful in shellscript where depending upon configuration, I might be mounting 15-20 volumes. 11.04 or previous versions, did notice the change, but did not grab the focus or pop up a new window.

How do I disable file manager notification about newly mounted drive?

[Edit]
At first I thought it was same nautilus instance that was grabbing the focus. Turns out I was wrong. I have almost 25 windows open. Thanks to killall, I could clean it quickly.

---

### Post by niranjan_rao on 2011-10-23
Anyone? Please help.

---

