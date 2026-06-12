---
title: "Visual effects problem"
date: 2009-08-27
forum: General Help
---

### Post by Shiv4m on 2009-08-27
Well a few days ago I was trying to setup a new theme because I was tired of my Mac OSX 10 theme. I by mistake pressed the no animations button and it took off all the animation on my ubuntu. Now every time I try to change animation or set it to the previous one which was custom, it gives me this message saying it could not be enabled. Could someone help please? Thanks.

[IMG]http://img406.imageshack.us/img406/3144/screenshotcfl.png

---

### Post by NoaHall on 2009-08-27
System -> Admin -> Hardware Drivers

Make sure your driver is the latest.

---

### Post by fela on 2009-08-27
Get the compiz-check script and run it.

What does

```
compiz --replace
```

in the terminal yield?

---

### Post by Shiv4m on 2009-08-27
Tried both of the suggestions and didn't work:

[IMG]http://img525.imageshack.us/img525/4645/screenshotshivamshivaml.png[/IMG]

---

### Post by fela on 2009-08-28
OK, did you get the compiz-check script? If not, download that and run it. Then post the output.

---

### Post by P4man on 2009-08-28
a compositing manager is already running. Probably that that Mac OS-x theme set it up. Type this in a terminal

```
gconftool-2 --type bool --set /apps/metacity/general/compositing_manager false

```

and try again. (may need to restart X)

---

### Post by Shiv4m on 2009-09-01
Thanks, it's all fixed now.

---

