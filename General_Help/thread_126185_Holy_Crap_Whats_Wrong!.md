---
title: "Holy Crap Whats Wrong!"
date: 2006-02-05
forum: General Help
---

### Post by Quackduck on 2006-02-05
This happens when I try to install and or I use the live cd. Any one help??? tryed 2 computers both do it.

:confused: :confused: :confused: 

[http://i17.photobucket.com/albums/b98/JunkyQuack/DSCN0054.jpg]("http://i17.photobucket.com/albums/b98/JunkyQuack/DSCN0054.jpg")

---

### Post by Mustard on 2006-02-05
Sure.  I've had that screen a few times when I misconfigured my xorg.conf, or didnt install my graphics drivers correctly.  On a regular install, I would use this command to reconfigure my system to use vesa drivers...

```
sudo dpkg-reconfigure xserver-xorg
```

What type of computers are you installing on ie graphics card, cpu etc?

---

### Post by Quackduck on 2006-02-05
OK so i figured out how to change the display setting but I do not know how to start linux from the command prompt.

Any help?

---

### Post by Ocxic on 2006-02-05
linux is alresy on, that's how you get to use the command prompt. you mean start the display manger. just type: startx   and it should startup so you can login and have a nice gui

---

