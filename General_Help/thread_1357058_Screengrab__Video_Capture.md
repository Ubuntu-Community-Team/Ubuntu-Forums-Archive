---
title: "Screengrab / Video Capture"
date: 2009-12-16
forum: General Help
---

### Post by cancer10 on 2009-12-16
Hi

I was wondering if there is any similar software like snagit for ubuntu 9.04

[http://www.techsmith.com/screen-capture.asp](http://www.techsmith.com/screen-capture.asp)


Many thanks

---

### Post by spiderbatdad on 2009-12-16
In synaptic package manager...System>>Administration>>Synaptic Package Manger there is gtk-recordmydesktop. It works pretty well.

---

### Post by cancer10 on 2009-12-16
ok will give it a try.

Quick question: is there anyway to remove the "Recent Documents" under "Places" on the Top panel?

---

### Post by spiderbatdad on 2009-12-16
checkout this thread. especially the last page.
[http://ubuntuforums.org/showthread.php?t=91154&page=3](http://ubuntuforums.org/showthread.php?t=91154&page=3)

---

### Post by cancer10 on 2009-12-17
> **spiderbatdad said:**
> checkout this thread. especially the last page.
[http://ubuntuforums.org/showthread.php?t=91154&page=3](http://ubuntuforums.org/showthread.php?t=91154&page=3)

When I ran the following command
```

sudo chattr +i recently-used.xbel
```


and entered my password.... 


I got the following message:

```
chattr: No such file or directory while trying to stat recently-used.xbel
```



Any idea whats happening?

---

### Post by spiderbatdad on 2009-12-17
sure. it's a hidden file ~/.recently-used.xbel

---

### Post by cancer10 on 2009-12-17
sudo chattr +i ~/.recently-used.xbel


That worked like a charm :)


Many thanks

---

