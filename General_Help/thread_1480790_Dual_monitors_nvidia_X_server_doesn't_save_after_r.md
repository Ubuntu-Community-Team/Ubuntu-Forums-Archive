---
title: "Dual monitors nvidia X server doesn't save after restart"
date: 2010-05-11
forum: General Help
---

### Post by nal13 on 2010-05-11
I have dual monitors running successfully with my BFG GeForce 8400GS and NVIDIA X server settings. The only problem is every time I restart, the settings go back to default, so I have to setup the dual monitors again. Can anyone help?

---

### Post by overdrank on 2010-05-11
Hi and have you tried saving the settings with 
```
gksu nvidia-settings
```

---

### Post by fooman on 2010-05-11
you must configure the settings as "root" (sudo) and save to x configuration file to make them "stick".

open a terminal and type:

```
gksudo nvidia-settings
```configure the monitors,  press "apply",  then press "save to x configuration file"

that should work.

edit: too slow,  overdrank beat me to it.

---

### Post by nal13 on 2010-05-11
Thanks guys, I will try that and get back to you. :)

---

### Post by nal13 on 2010-05-11
Ok, got it, thank you so much. I wasn't doing the "save to x configuration file" part.

---

### Post by markbl on 2010-05-12
This is a trivial issue to fix but was a problem when 9.04 and 9.10 came out. It stumps and confuses many, particularly new users. I find it astounding that this bug has not been fixed yet!?

---

