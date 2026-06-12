---
title: "Ubuntu won't shutdown (or even close the desktop)"
date: 2011-01-14
forum: General Help
---

### Post by chriseid on 2011-01-14
I've done about as much research as I can and all I've been able to find is problems once the desktop is closed. In my case Ubuntu will close its UI but the desktop background will remain visible then it will hand there forever. How can I fix this?

My Specs:
Intel Atom 1.8
Nvidia ION
2GB DDR3
320GB HDD
Ubuntu 10.10

Thanks for your help!

---

### Post by Grenage on 2011-01-14
Does it shut down from the terminal? If not, does it give you any feedback?

From a terminal:

```
sudo shutdown -h -P now
```

This 'might' be all you need in ubuntu:
```
sudo shutdown
```

---

### Post by Grenage on 2011-01-14
[Duplicate post.]

---

### Post by chriseid on 2011-01-14
Thanks for the help but that didn't do the trick. I'm still just left looking at my wallpaper with the system hanging.  Is there an error log somewhere that may help diagnose the problem?

---

### Post by Grenage on 2011-01-14
/var/log/messages may hold some answers?

---

