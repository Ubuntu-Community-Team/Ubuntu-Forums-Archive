---
title: "Panel is not where it should be"
date: 2009-06-27
forum: General Help
---

### Post by marcelluspye on 2009-06-27
I was trying to get a better view from the screen size of my laptop, and tried dragging the panels to the left and right. However, I didn't know this would turn the writing sideways and make it hard for me to see the time and use the panel in many of its functions. However, when I went to the panel properties, it did not allow me to move it again, like seen in the picture attached. How do I fix this?

---

### Post by mhgsys on 2009-06-27
just press alt and mouse click on the panel, 
You can drag it up again.

---

### Post by kokkus on 2009-06-27
Right click on the panel and unmark "look the panel" or whatever it says.
In Version 8 if I remember right, it should be possible to simply drag the panel to wherever you want it to be.
In Version 9 you have to use alt+mouse.

---

### Post by CatKiller on 2009-06-27
> **kokkus said:**
> In Version 9 you have to use alt+mouse.

No you don't. It's middle-click and drag, the same as the panel applets. And it's 9.04, because it was released in April. There isn't a Version 9. There will be a 9.10 in October.

---

### Post by marcelluspye on 2009-06-27
I've tried all of these, with different mouses. However, none of them worked. I am running this on a netbook, so my laptop might have the netbook remix, but I'm not sure about that. What I do know is that my laptop is running Ubuntu 8.0.4.. Is there any authorization I can grant myself so that I can select it from the menu in the picture?

---

### Post by mhgsys on 2009-06-27
Well, If nothing works you could open a terminal and type

```

gconftool-2 --recursive-unset /apps/panel 

```

and restart gdm after that

in console (Ctrl+Alt+f1 ,f2, f3, etc) type
```
 
sudo /etc/init.d/gdm stop

```
```

sudo /etc/init.d/gdm start

```

---

### Post by marcelluspye on 2009-06-27
Thanks, that did help. I'm not sure why the way the support says to do it(simply dragging the panel) didn't work though.

---

### Post by mhgsys on 2009-06-27
me neither, 

But at least you've got your panels back in place.

---

