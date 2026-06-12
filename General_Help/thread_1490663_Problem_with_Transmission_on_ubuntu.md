---
title: "Problem with Transmission on ubuntu"
date: 2010-05-22
forum: General Help
---

### Post by ryosaeb4 on 2010-05-22
Hi to everybody,

I've a big problem with Transmission on Ubuntu.
The transmission application can't start.

I have do this



System -> Amministration ->  System Monitor

I can see that "Transmission" is in sleeping. I've tryed to killed the application and restart it, but transmission back to sleeping time!

how I can do to restart transmission?

---

### Post by SlidingHorn on 2010-05-22
> **ryosaeb4 said:**
> Hi to everybody,

I've a big problem with Transmission on Ubuntu.
The transmission application can't start.

I have do this



System -> Amministration ->  System Monitor

I can see that "Transmission" is in sleeping. I've tryed to killed the application and restart it, but transmission back to sleeping time!

how I can do to restart transmission?

Kill it again, then start it from your terminal.  Post any errors it gives you on here.

---

### Post by ryosaeb4 on 2010-05-22
I'm a mac user, I don't know how to start it from terminal.
Can you say to me the commands?

thanks

---

### Post by SlidingHorn on 2010-05-22
just type into the terminal:

```
transmission
```

and hit Enter

---

### Post by ryosaeb4 on 2010-05-22
Look this capture screen :D 

No error... just transmission in sleeping again

Edit bobhi.zazen: removed large image. Please use thumnails / hotlinks.

[http://www.walterfantauzzi.com/files/FORUM/Schermata-2010-05-22-a-21.52.19.jpg]("http://www.walterfantauzzi.com/files/FORUM/Schermata-2010-05-22-a-21.52.19.jpg")

---

### Post by kerry_s on 2010-05-22
i would guess you did not enable the tray icon.

---

### Post by kerry_s on 2010-05-22
looking in the ~/.config/transmission, what i would do is grab a copy of torrent,resume & incomplete folders, so you don't lose your download, then delete everything, start transmission & set it up, make sure you turn on the icon.

---

