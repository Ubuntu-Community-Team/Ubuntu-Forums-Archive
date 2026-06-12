---
title: "Top bar with icons not full width"
date: 2009-11-15
forum: General Help
---

### Post by tomsax on 2009-11-15
Through looking for ways to deal with another problem I seem to have reduced the bar at the top (with applicaion, quit icon, etc) to a smaller width and can't put it back to how it was.  I seem to be able to move and and make it bigger but not change its width.

Help!

Tom

---

### Post by sisco311 on 2009-11-15
Right Click -> Customize Panel... -> instead of *Normal Width* select *Full Width*

---

### Post by tomsax on 2009-11-15
I don't seem to have that on my option but I realise the window may be cropped due to the problem in my other recent post.  I have the option of fixed position and freely moveable but not full width.

Tom

---

### Post by joeyknuccione on 2009-11-15
> **tomsax said:**
> I don't seem to have that on my option but I realise the window may be cropped due to the problem in my other recent post.  I have the option of fixed position and freely moveable but not full width.

Tom
Not sure about Xubuntu, but on my 9.10 Gnome...

Right click within the panel > Properties > Expand

---

### Post by sisco311 on 2009-11-15
> **tomsax said:**
> I don't seem to have that on my option but I realise the window may be cropped due to the problem in my other recent post.  I have the option of fixed position and freely moveable but not full width.

Tom

edit the config file:
```
mousepad ~/.config/xfce4/panel/panels.xml
```

and replace:
```
<property name="fullwidth" value="0"/>
```
with
```
<property name="fullwidth" value="1"/>
```

restart the panel:
```
killall xfce4-panel
```

if the panel doesn't restart, press Alt+F2 and run:
```
xfce4-panel
```

---

