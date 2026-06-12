---
title: "Mozilla firefox running but not responding..."
date: 2011-10-18
forum: General Help
---

### Post by Bluehotdog5 on 2011-10-18
whenever I try to start up Mozilla Firefox it tells me to exit the existing process or restart, even though I don't have it open.

In windows this is a simple fix, just go to the list of processes and end it manually. But I have no idea how to do that here. I tried killall firefox and it said there is no firefox process.

any idea's?

---

### Post by ajgreeny on 2011-10-18
> **Bluehotdog5 said:**
> whenever I try to start up Mozilla Firefox it tells me to exit the existing process or restart, even though I don't have it open.

In windows this is a simple fix, just go to the list of processes and end it manually. But I have no idea how to do that here. I tried killall firefox and it said there is no firefox process.

any idea's?
Try ```
killall firefox-bin
```
Sometimes, for some weird reason,  it is that executable that gets stuck, not just plain firefox.  You could test this first with ```
ps aux | grep firefox
```to see if it shows it running.

---

### Post by Bluehotdog5 on 2011-10-18
> **ajgreeny said:**
> Try ```
killall firefox-bin
```
Sometimes, for some weird reason,  it is that executable that gets stuck, not just plain firefox.  You could test this first with ```
ps aux | grep firefox
```to see if it shows it running.

thanks, that did it

---

