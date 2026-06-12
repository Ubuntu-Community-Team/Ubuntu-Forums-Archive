---
title: "Swapping keys using xmodmap"
date: 2010-06-06
forum: General Help
---

### Post by peterhaagerup on 2010-06-06
I am using an Apple Keyboard (DK-layout) on my PC running Ubuntu 10.4.

The problem: My key used to type <, > and \ is swapped with the key used to type ½, § and ¾. If I connect a standard PC-keyboard with DK-layout using USB, it works just fine.

The problem exists both in the console and X. I solved the problem in the console by installing the console-keymaps package, made a copy of dk-latin1.kmap.gz and swapping keycode 86 with keycode 41 and loading the new keymap with the loadkeys command. I only need to figure out how to load the new keymap at boot time.

However, in X, I want to do exactly the same. I suppose I have to use Xmodmap. I simply can't figure out how to do it. Any ideas or solutions?

---

### Post by drs305 on 2010-06-06
I use a startup script to change one of my keys.

In System, Preferences, Startup Applications I've added a link to my startup script. In the script, I have this entry to change one of the keys:
> 
xmodmap -e 'keycode 82=Tab'


You can use an app/command called "xev" to determine the keycodes if you don't already have them.

---

### Post by peterhaagerup on 2010-06-06
Thank you very much. I found out how export current xmodmap layout:

xmodmap -pke > modmap

I used xev to find the keycodes and in the exported file I found these lines:

keycode  49 = onehalf section onehalf section threequarters paragraph
keycode  94 = less greater less greater backslash notsign

so I made an .Xmodmap file with the lines

keycode  94 = onehalf section onehalf section threequarters paragraph
keycode  49 = less greater less greater backslash notsign

and - now it works! :-)

Thank you very much.

Now I only need to find out how to load the console keymap at boot time.

---

### Post by DirtyPC on 2010-10-30
> **peterhaagerup said:**
> Thank you very much. I found out how export current xmodmap layout:

xmodmap -pke > modmap

I used xev to find the keycodes and in the exported file I found these lines:

keycode  49 = onehalf section onehalf section threequarters paragraph
keycode  94 = less greater less greater backslash notsign

so I made an .Xmodmap file with the lines

keycode  94 = onehalf section onehalf section threequarters paragraph
keycode  49 = less greater less greater backslash notsign

and - now it works! :-)

Thank you very much.

Now I only need to find out how to load the console keymap at boot time.
To this at boot time, open a text editor enter and save the above codes as a .xmodmap.rc file in your home directory. It will then load everytime at boot.

---

