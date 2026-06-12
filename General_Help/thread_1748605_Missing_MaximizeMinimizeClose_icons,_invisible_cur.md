---
title: "Missing Maximize/Minimize/Close icons, invisible cursor"
date: 2011-05-03
forum: General Help
---

### Post by Lipooo on 2011-05-03
I am new. I have installed recently a bunch of distros and settled with xubuntu 11.04 for my old laptop. Everything worked fine out of the box except some times wireless stopped working and the pc needed a restart. One of those times i restarted and because restart seemed unresponsive I clicked again but a problem tab poped up. Every time that i clicked restart, the pop up appeard I was forced to force shutdown.

Now...
1. Maximize/Minimize/Close buttons are completly missing. Even windows settings (where you can unjust those buttons) does not work. It is blank.

2. Cursor is invisible but when i click something appears , stays visible but the cursor is a different icon than before.

3. other problems as well. I cannot move terminal etc...

---

### Post by JanisL on 2011-06-19
I am having this exact same problem with Xubuntu running on a Lenovo laptop.

---

### Post by Toz on 2011-06-19
Looks like the window manager isn't working. Press Alt+F2 and type in:```
xfwm4 --replace
```

Does everything improve? If so, and if you lose everything again the next time you login, you will need to add that command to your autostart.

---

### Post by rulorojo on 2011-10-23
Bravo, had the same problem !
thank you!

---

### Post by theprophet84 on 2012-02-14
Thanks, you just saved me from having to turn in my Comp. Sci. homework.  The teacher overlooks my apathy if I fix his computer.

---

### Post by amarad on 2013-01-03
Thank you very much, very helpful. I had the same problem after installing KDE KMahjongg on my Acer Aspire One notebook, running with XUbuntu 12.10 with Xfce4.10 Environment and your little trick solved it miraculously :)

---

### Post by cmcanulty on 2013-01-03
I've had that happen on gnome classic and ended up reinstalling is there a similar command for classic?

---

### Post by ibrahimjackson on 2013-04-06
Thanks!  I'll be keeping this handy!):P

---

