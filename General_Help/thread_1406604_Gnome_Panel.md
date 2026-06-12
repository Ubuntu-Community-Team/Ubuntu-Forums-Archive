---
title: "Gnome Panel"
date: 2010-02-14
forum: General Help
---

### Post by robbie2685 on 2010-02-14
Hi there...
New to ubuntu 9.10...
so far very happy with the way it is wrking..
here is the deal..i movd the gnome panel on the right side of the screen and it was hidden...but after few minutes i lost the panel...
need help...

---

### Post by wojox on 2010-02-14
Hit Alt + F2 and enter:

```
gconf-editor
```

Go to apps/panel/toplevels/ and adjust in there.

---

### Post by mhgsys on 2010-02-14
open up a terminal

```
sudo killall gnome-panel
```

and then

```
gnome-panel
``` to start it again.

You can also restore the original panel with 


```
gconftool-2 --recursive-unset /apps/panel
```

and restart gdm after that

go to console (Ctrl+Alt+f1 ,f2, f3, etc) type



```
sudo /etc/init.d/gdm stop
```



```
sudo /etc/init.d/gdm start
```

---

### Post by robbie2685 on 2010-02-14
Thank you very much...
appreciated....

---

### Post by mhgsys on 2010-02-14
I wondered; 

Did you go with the commands wojox gave you or did you end up restoring the original panel?

---

