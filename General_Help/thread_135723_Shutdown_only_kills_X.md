---
title: "Shutdown only kills X?"
date: 2006-02-24
forum: General Help
---

### Post by Herd on 2006-02-24
sudo shutdown in console just kills x and takes me to a terminal.  How do I actually shutdown?  Thanks.

---

### Post by dotman on 2006-02-24
you can use

```
sudo shutdown -hP now
```

if you want to see all of the shutdown options use

```
sudo shutdown --help
```

---

### Post by Skeletonix on 2006-02-24
reboot: sudo shutdown -r now
halt: sudo shutdown -h now

---

