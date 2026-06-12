---
title: "Conky disappears when I clike the desktop in Gnome Shell"
date: 2011-11-25
forum: General Help
---

### Post by DobsonM on 2011-11-25
I am using Ubuntu 11.10 with Gnome shell, everytime I click the desktop my conky vanishes, what setting should I have in my conky config to stop this happening?  It is set at own_window_type desktop at the moment.

Any help would be greatly appreciated.

---

### Post by Frogs Hair on 2011-11-25
You could try own_window_type override , but this may make any  border or shadows around conky transparent . Also try own_window_type conky .

---

### Post by DobsonM on 2011-11-25
Thanks man, the own_window_type conky worked perfectly.

---

### Post by DobsonM on 2011-11-25
Now Conky covers my covergloobus :(  grrrr

Can anyone help with this?

---

### Post by DobsonM on 2011-11-25
Anyone?

---

### Post by Frogs Hair on 2011-11-25
I only use Gloobus Preview , so I can't help with that .

---

### Post by stinkeye on 2011-11-26
> **Frogs Hair said:**
> You could try own_window_type override , but this may make any  border or shadows around conky transparent . Also try own_window_type conky .
There is no 
```
own_window_type **conky**
```

it will revert to 
```
own_window_type normal
```

and needs the hints specified
eg
```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

> Now Conky covers my covergloobus  grrrr

 Can anyone help with this?
```
own_window_type override
```
may work or you may have to move to different area of the desktop.

Could also experiment by using gnome-tweak-tool to turn off nautilus drawing the
desktop and different **own_window_type** settings.

---

