---
title: "webcam/built in mic drivers"
date: 2009-10-03
forum: General Help
---

### Post by Guy Sibley on 2009-10-03
I have been searching google for quite some time and I can't find drivers for my built in webcam/microphone. Are there drivers for these types of devices available for ubuntu?
Thank you for you help.

---

### Post by 3rdalbum on 2009-10-03
> **Guy Sibley said:**
> I have been searching google for quite some time and I can't find drivers for my built in webcam/microphone. Are there drivers for these types of devices available for ubuntu?
Thank you for you help.

They are usually built-in (you should always try to buy a webcam that uses UVC; it's a standard driver on all operating systems) but if they're not present then it can sometimes be possible to find a driver.

Can you please give us the output of:

```
lsusb
```

and hopefully it should yield enough information to find a driver.

---

