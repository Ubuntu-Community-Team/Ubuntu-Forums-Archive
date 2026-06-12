---
title: "panel appears in middle of screen"
date: 2010-03-10
forum: General Help
---

### Post by kainalu on 2010-03-10
Hello All,


Got a little problem. I tried to set my panel to the right side. That looked ugly so I put it back up top. Now, every time I log in, my panel appears in the middle of the screen, and totally cluttered up. I have to hit expand on (which puts it back up top), re-arrange everything, and turn expand off. It stays all pretty until I log back in, then messes up again.

any Ideas?
THANKS!

---

### Post by apexofservice on 2010-04-05
Bump. 

Same issue for me.

---

### Post by r_s on 2010-04-05
delete the directory .gnome in your home folder and it will restore the desktop to default , later on you can modify it as you want.

---

### Post by bonfire89 on 2010-07-30
I also have this problem. (10.04)

---

### Post by kainalu on 2010-07-31
I ended up solving this by deleting all my panels, making new ones, stocking them how I like them, and then using gconf-editor to lock them in place. 

To use gconf editor to lock panels:
press Alt+f2
type gconf-editor, press enter
navigate to  apps/panel/global
click locked_down on

hope that helps!

--kainalu

---

