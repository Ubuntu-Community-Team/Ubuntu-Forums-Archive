---
title: "Start an alternate X session"
date: 2010-12-19
forum: General Help
---

### Post by theanalyst on 2010-12-19
How do i start an alternate X session in ubuntu...generally Ctrl + Alt + F7-F11 is reserved for alternate X sessions right. If I open a tty1 and do something like xinit -- :1 I guess I have something like an X session but it doesn't have any desktop environment like Gnome...what i want to do is if I am running a fullscreen game or something in Xsession:0 can I do something else in a new Xsession? I hope my question is clear

---

### Post by tredegar on 2010-12-19
Click the button that normally lets you turn off your computer
Choose "Switch from theanalyst"
Login as someone else.
You can switch back to your original session my clicking the button again, and selecting the session from the list.

---

### Post by nothingspecial on 2010-12-19
Try
```

startx -- :1
```

---

