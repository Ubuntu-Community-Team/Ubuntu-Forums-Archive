---
title: "Symlink from /dev/ttyUSB0 to .wine/dosdevices/com1"
date: 2009-12-11
forum: General Help
---

### Post by brettybaby on 2009-12-11
>>?

---

### Post by Ylon on 2009-12-11
> **brettybaby said:**
> Just have to make a symlink from  /dev/ttyUSB0 to  .wine/dosdevices/com1

How is this done?
Didn't try, but
**sudo ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1**
make the job?

---

### Post by crolanx on 2009-12-11
Hi,

you could try
```
sudo ln -sf /dev/ttyUSB0 /home/<YOUR USERNAME>/wine/dosdevices/com1
```.

But please be aware that **udev** will probably replace it the next time you boot your Computer.

---

### Post by brettybaby on 2010-07-26
neither code worked!

---

