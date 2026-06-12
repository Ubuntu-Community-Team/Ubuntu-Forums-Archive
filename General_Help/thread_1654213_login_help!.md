---
title: "login help!"
date: 2010-12-28
forum: General Help
---

### Post by mmsmc on 2010-12-28
i just activated a nivdia graphics driver and restarted my computer and now when i turn on my computer it puts me right into the tty mode, no desktop

---

### Post by mikewhatever on 2010-12-28
Well, the tty mode offers a login prompt, just type your username and password to login.
:p

---

### Post by mmsmc on 2010-12-28
i did that, it turns into a terminal and cant get out of it, if i input exit it puts me into anoother tty(tty2-10) and if i put cntrl alt f7,6,1 it puts me into another tty

---

### Post by mikewhatever on 2010-12-28
Apparently, there is no problem with logging in, so what can it be? ...
Is it the lack of GUI (Graphical User Interface) instead of login?

---

### Post by karthick87 on 2010-12-28
On booting hold down the shift key and the grub menu will appear. The Ubuntu system should be highlighted on the menu. You should press the "e" key and on the new screen navigate to the end of the line that says "quiet splash" and remove those words and replace them with "nomodeset"  without the quotes  then press Ctrl + X to reboot.

---

### Post by EifleMan on 2010-12-28
After logging in on your tty prompt, did you try entering "startx"? If not, try it, and post the result if you're not presented with a GUI.

---

### Post by mmsmc on 2010-12-28
it saysfatal error no screens found

---

### Post by karthick87 on 2010-12-28
Did you tried post #5 ?

---

### Post by mmsmc on 2010-12-28
> **karthick87 said:**
> On booting hold down the shift key and the grub menu will appear. The Ubuntu system should be highlighted on the menu. You should press the "e" key and on the new screen navigate to the end of the line that says "quiet splash" and remove those words and replace them with "nomodeset"  without the quotes  then press Ctrl + X to reboot.


when i do this it just puts me back into tty

---

### Post by karthick87 on 2010-12-28
Try,
```
sudo /etc/init.d/gdm start
```

---

### Post by mmsmc on 2010-12-28
at work now, try as soon as i get home

---

### Post by mmsmc on 2010-12-28
no command found

---

