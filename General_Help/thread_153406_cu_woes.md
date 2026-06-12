---
title: "cu woes"
date: 2006-03-31
forum: General Help
---

### Post by saphire_2001 on 2006-03-31
Hey guys,

I have a Solaris box that is only accessible (at this moment) through a serial connection.  I have everything hooked up and I installed uucp to give me access to the cu utility.  On other systems, especially my old redhat system, if I typed
```

cu -l /dev/ttyS0

```
It would connect me to the other computer without an issue.  My guess is that I'm using the wrong device or I'm missing a module to let me use my serial port.  dmesg is not being particularly helpful either.  Anyone have any suggestions?

---

