---
title: "dxdiag or command to output current computer specs?"
date: 2012-07-01
forum: General Help
---

### Post by ryanyeah on 2012-07-01
Dxdiag in windows does a good job of outputting amount of ram, CPU etc. of the current system. Is there an equivalent command similiar to this for linux systems? Ideally I guess it would be similar to df -h, but not just for disk space.

---

### Post by ubudog on 2012-07-01
Check out the system monitor that comes with Ubuntu.  Also, check out 'hardinfo':
```
sudo apt-get install hardinfo
```

and then to run:
```
hardinfo
```

If you need a completely command-line based tool, check out 'hwinfo'.
```
sudo apt-get install hwinfo
```
```
hwinfo
```

---

### Post by stinkeye on 2012-07-01
....or
```
sudo lshw -html > ~/hardwarespecs.html
```
Creates a html file in your home folder.

---

### Post by ryanyeah on 2012-07-01
> **ubudog said:**
> Check out

Thanks!!

---

