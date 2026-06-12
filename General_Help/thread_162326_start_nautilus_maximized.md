---
title: "start nautilus maximized?"
date: 2006-04-18
forum: General Help
---

### Post by lezz on 2006-04-18
do you guys know how to start nautilus maximezed from the command shell? i've looked in the man page but couldnt find any appropiate option. all methods are accepted.

---

### Post by 23meg on 2006-04-18
I'm not sure if this is the most practical way but you can use the --geometry option to do it. Refer to the manpage for X for the X geometry specification.

---

### Post by lezz on 2006-04-18
[QUOTE=23meg]I'm not sure if this is the most practical way but you can use the --geometry option to do it. Refer to the manpage for X for the X geometry specification.[/QUOTE]

yeah, i've already done that but it didn't help. i ran:

nautilus --geometry=400x400 &
nautilus --geometry=200x200 &
nautilus --geometry=400x800 &
nautilus --geometry=1500x2000 &

but all windows that poped up had exactly the same size. weird. is it the same for you?

---

### Post by z_diver on 2006-04-18
[QUOTE=lezz]yeah, i've already done that but it didn't help. i ran:

nautilus --geometry=400x400 &
nautilus --geometry=200x200 &
nautilus --geometry=400x800 &
nautilus --geometry=1500x2000 &

but all windows that poped up had exactly the same size. weird. is it the same for you?[/QUOTE]
Running any of the commands above I get the same size window as the last completely terminated nautilus session, unless that session terminated with a maximized window, in which case I get the size of the previously terminated nautilus session.

So I can produce a *[COLOR="DarkRed"]nearly[/COLOR]* maximized window by resizing the last open nautilus window to it's limits, then closing it and running: [COLOR="Blue"]nautilus &[/COLOR]. Note: This is accomplished by stretching it and closing, not using the maximize button.

Not sure if this is going to be helpful if you are writing a script however.

---

### Post by lezz on 2006-04-19
finally i know how this is beeing done.

install wmctrl and use it to maximize your windows!

---

### Post by shuttleworthwannabe on 2006-04-19
so what is wmctrl supposed to do: double clicking on the border maximises instantaly???

---

