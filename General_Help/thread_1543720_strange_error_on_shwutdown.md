---
title: "strange error on shwutdown"
date: 2010-08-01
forum: General Help
---

### Post by nodnolse1 on 2010-08-01
When i shutdown or restart, i get this error [http://img130.imageshack.us/i/61996702.png/](http://img130.imageshack.us/i/61996702.png/)

it says that an applications its running, but all is closed

here my top processes [http://paste.ubuntu.com/471917/](http://paste.ubuntu.com/471917/)

please help to understand what is the applications that running because the pop-up says "unknown applications", top semms regular to me. what is it this application??????

Thank you in advance, Paolo

---

### Post by jerenept on 2010-08-01
You are still running Leafpad. It is a text editor. Ensure that you save your work and exit Leafpad before shutting down.

---

### Post by nodnolse1 on 2010-08-01
thank you for the answer. But,  how do you understand that is exactly leftpad? i searched alone and i havent seen nothingh strane in top

---

### Post by oleink on 2010-08-01
> **nodnolse1 said:**
> thank you for the answer. But,  how do you understand that is exactly leftpad? i searched alone and i havent seen nothingh strane in top

yeah it doesn't say its leafpad..?  It said that for me when I had google chromium still running once with identical looks.

---

### Post by oleink on 2010-08-02
> **nodnolse1 said:**
> thank you for the answer. But,  how do you understand that is exactly leftpad? i searched alone and i havent seen nothingh strane in top

quick question:  Have you changed anything at all since before this happened

---

### Post by nodnolse1 on 2010-08-02
Unfortunately I change many settings an program every day ...

---

### Post by oleink on 2010-08-03
> **nodnolse1 said:**
> Unfortunately I change many settings an program every day ...

But was it something major like a grub change or something like that?  Either that or major settings change

---

### Post by JBAlaska on 2010-08-03
try opening a terminal and typing:
```
sudo reboot
```

You may get some verbose feedback that way.

---

