---
title: "Find device usb is tied to"
date: 2011-04-09
forum: General Help
---

### Post by ntesla123 on 2011-04-09
How do I find the device that a usb stick is tied to (eg. /dev/sdc)

---

### Post by 5149.5 on 2011-04-09
There are several ways to find that but Disk Utility has a good combination of functions for  USB sticks.

---

### Post by Ghost_Mazal on 2011-04-09
If you type in terminal

```
df -h
```

It will show all mounted devices.
I think that is the quickest way.

---

### Post by HermanAB on 2011-04-09
These two:
$ mount
$ df

---

