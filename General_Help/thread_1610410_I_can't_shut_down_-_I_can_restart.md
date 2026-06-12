---
title: "I can't shut down - I can restart"
date: 2010-10-31
forum: General Help
---

### Post by complience on 2010-10-31
I have another strange problem with ubuntu 10.10

When I select shutdown the system hangs at the plymouth screen on the unmount local file system stage.

but if i restart the process is sucessfull, what additional steps are carried out during a fullshut down that might cause this error?

---

### Post by TeoBigusGeekus on 2010-11-01
When the system hangs down, can you switch to tty1 (Ctrl+Alt+F1) to see if there are any error messages?

---

### Post by complience on 2010-11-01
nope.. the system is hung.

Unmounting Local file systems

*/ Mount is busy

... then nothing - seems its a big problem of 10.10

---

### Post by complience on 2010-11-09
bump - anyone got a resolution?

---

### Post by lordskid on 2010-11-09
All I know is that I have that same problem with 10.04 on an acer travelmate 3210. do you happen to be using an acer machine?

---

### Post by lordskid on 2010-11-09
I usually just restart my laptop then press the power button when the POST logo appears

---

### Post by complience on 2010-11-09
no not acer

---

### Post by alphaamanitin on 2010-11-09
Try this at the command line:
```
sudo shutdown -P now
```shutdown brings down the OS and -P powers the computer off, now is well, do it now.  I always find it worth it to try things at the command line; I have had occasions where my GUI buttons stop working but my  command lines will still do the job.

AlphaA

---

