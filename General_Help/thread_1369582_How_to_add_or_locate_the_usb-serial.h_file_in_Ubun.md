---
title: "How to add or locate the usb-serial.h file in Ubuntu"
date: 2010-01-01
forum: General Help
---

### Post by lnarasimhan on 2010-01-01
Hello,

I am trying to get the ti_usb_3410_5052.ko driver installed but it gives a an error saying that "cannot locate the usb-serial.h file."  Kindly let me know how to over come this problem. I saw in this forum about a patch but it is not working.

Thanks in Advance.
LN

---

### Post by Barriehie on 2010-01-01
From a terminal you can use the find command:
```

sudo find / -iname usb-serial.h -print

```

---

### Post by Barriehie on 2010-01-02
So, did you find it???

---

