---
title: "Slow boot time"
date: 2011-02-16
forum: General Help
---

### Post by piymon on 2011-02-16
Ibrought a hp laptop g42-460tu
and installed ubuntu 10.10 64 bit on it.
Initially the boot time was fast but suddenly it has became annoyingly slow. How can i make it fast

---

### Post by piymon on 2011-02-16
help me please

---

### Post by NightwishFan on 2011-02-16
Sure, I shall do my best to help. First off, the best way to evaluate boot time is the software called boot chart. This will explain how to use it:
[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

Note about the output, it should be an image file that shows a chart. Simply uploading the image file will cause it to be re-sized. You will need to compress it into a .tar.gz (which is easy as right click -> compress on Ubuntu).

You should also compress to tar.gz the file /var/log/dmesg and upload here.

We can go from there.

---

### Post by piymon on 2011-02-16
> **NightwishFan said:**
> Sure, I shall do my best to help. First off, the best way to evaluate boot time is the software called boot chart. This will explain how to use it:
[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

Note about the output, it should be an image file that shows a chart. Simply uploading the image file will cause it to be re-sized. You will need to compress it into a .tar.gz (which is easy as right click -> compress on Ubuntu).

You should also compress to tar.gz the file /var/log/dmesg and upload here.

We can go from there.


here u go..

---

### Post by NightwishFan on 2011-02-16
I analyzed both files and it seems nothing is very unusual. Your boot time is around 36 seconds which seems entirely normal and I doubt it was significantly faster than that before. Was it much much faster?

There seems to be a gap here:
```
[    0.273230] Booting Node   0, Processors  #1 #2 #3
[    0.812149] Brought up 4 CPUs
```

Not sure exactly what time increment dmesg uses though, and such a low level issue is beyond my expertise any way. Perhaps someone more experienced will review this thread. In that case it is good to have this information available. I will surely get back to you if I find any more information.

---

### Post by piymon on 2011-02-16
> **NightwishFan said:**
> I analyzed both files and it seems nothing is very unusual. Your boot time is around 36 seconds which seems entirely normal and I doubt it was significantly faster than that before. Was it much much faster?

There seems to be a gap here:
```
[    0.273230] Booting Node   0, Processors  #1 #2 #3
[    0.812149] Brought up 4 CPUs
```

Not sure exactly what time increment dmesg uses though, and such a low level issue is beyond my expertise any way. Perhaps someone more experienced will review this thread. In that case it is good to have this information available. I will surely get back to you if I find any more information.


thanks for your time and yes it was earlier around 10 seconds.

---

### Post by NightwishFan on 2011-02-16
Sorry I could not be of more help, I am not skilled much in these matters however I did not want to leave your post unanswered. As I said, I certainly will continue to look into it.

---

