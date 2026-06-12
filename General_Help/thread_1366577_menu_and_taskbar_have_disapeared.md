---
title: "menu and taskbar have disapeared"
date: 2009-12-28
forum: General Help
---

### Post by bigtel on 2009-12-28
Xubuntu 9.04 Kernel 2.6.28-17 Generic


I hope someone can help me - My taskbar and icons from around the screen have suddenly disapeared..! If I minimise a window, it totally disapears and the only way I can find it is Alt-Tab.

My internet connection has also stopped working and as i can not find any of my icons i can not sort it out.

Is there any reason this would happen? And how can i resolve this?

Help..!

---

### Post by s.fox on 2009-12-28
Hi,

Please try suggestions mentioned [here]("http://ubuntuforums.org/showpost.php?p=6642351&postcount=2"). :)

-Silver Fox

---

### Post by bigtel on 2009-12-28
Hi - tried that but within the terminal window it says - 

'gnome-terminal' is currently not installed'

Any other suggestions here?

---

### Post by fooman on 2009-12-28
> **bigtel said:**
> Hi - tried that but within the terminal window it says - 

'gnome-terminal' is currently not installed'

Any other suggestions here?

using xubuntu?  ....try pressing the alt-f2 keys and type the following into it:

```
xfce4-panel &
```

then click "run".

hope that helps.

---

### Post by bigtel on 2009-12-28
:):):)

Thats done it..!! great

:):):)

What caused this to happen then?

It's lucky I have a seperate laptop which I could use to ask this forum. This is not the first time i have been helped out of a sticky situation..!!

---

### Post by bigtel on 2010-02-19
After and upgrade of Firefox web browser this strange occurrence has happened again.I do not understand why my menu and icon should vanish in this way.

I located this post and the solution worked again like a charm. What is happening here then and what does 'xfce4-panel &' actually do..??

Thanks

BigTel

---

### Post by thinking2loud on 2010-02-21
What's happening?  Dunno.

What does "[*command*] &" mean:  run *command* as a background process (not attached to a terminal).

If this xfce4-panel & makes your panels come back, it implies something is shutting down the xfce4-panel process that is supposed to update them.

---

