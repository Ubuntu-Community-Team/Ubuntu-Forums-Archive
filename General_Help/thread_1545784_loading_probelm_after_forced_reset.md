---
title: "loading probelm after forced reset"
date: 2010-08-04
forum: General Help
---

### Post by sawibel on 2010-08-04
I didn't pay attention to the power level of my computer and it shut down automatically when it got down to 10%. I plugged it in and booted it back up, but Ubuntu wouldn't load! It got to the black screen with the cursor and stayed that way for 15 minutes before I gave up and loaded Windows instead. Any ideas?

EDIT: The cursor place is not a command window. I can type stuff in it, but once I hit enter nothing happens but a return.

---

### Post by linux18 on 2010-08-04
> **sawibel said:**
> I didn't pay attention to the power level of my computer and it shut down automatically when it got down to 10%. I plugged it in and booted it back up, but Ubuntu wouldn't load! It got to the black screen with the cursor and stayed that way for 15 minutes before I gave up and loaded Windows instead. Any ideas?

EDIT: The cursor place is not a command window. I can type stuff in it, but once I hit enter nothing happens but a return.
-choose recovery mode at grub
-drop to a root prompt 
-type "telinit 3" and logon
-type "xinit" 
-after it loads type "metacity &" (you may need to wiggle the mouse  before it registers)
-then type "gnome-panel & nm-applet &"
your good to go! a reboot will take you back into the normal DE

---

### Post by sawibel on 2010-08-04
How do I drop a root prompt? (I'm not very good with the operating part of computers.)

---

### Post by linux18 on 2010-08-04
> **sawibel said:**
> How do I drop a root prompt? (I'm not very good with the operating part of computers.)
its a menu option after you choose recovery mode at grub

---

### Post by sawibel on 2010-08-04
In that case I'm not sure I actually have grub. I think I have whatever windows uses to boot up. When I enter the recovery mode, text streams along for a while and then stops after a minute or so. There's a cursor there, but typing anything into it doesn't seem to do anything.

---

### Post by sawibel on 2010-08-04
So, any one have any ideas on how to fix this without grub? Would a live CD be helpful somehow? I do have one.

(Sorry if I'm not supposed to double-post, but I do need help and it seems my thread has been abandoned.)

---

### Post by linux18 on 2010-08-04
if you don't have grub or if you do and just don't know:

boot from the live cd, open a terminal, and type:

```
 sudo grub-install /dev/sda && sudo update-grub 
```

then reboot into recovery mode and  wait for the menu to pop up
 choose root from the recovery menu ( its usually the last option)
" telinit 3 "
" xinit "
you will get a black screen with a white terminal and mouse support
hover the mouse over the terminal and type " metacity &  gnome-panel & nm-applet & "
if you get prompted to install one of these components (usually gnome-panel) install it.
then " sudo reboot "

---

### Post by sawibel on 2010-08-05
Is there a way to do this without grub? Last time I installed grub it messed up my computer and I couldn't load windows either.

---

### Post by linux18 on 2010-08-05
> **sawibel said:**
> Is there a way to do this without grub? Last time I installed grub it messed up my computer and I couldn't load windows either.
Is this a wubi installation?
if not you must already have grub.

---

### Post by sawibel on 2010-08-06
It is a wubi installation. I have windows on my laptop and ubuntu loading from an external drive.

---

### Post by sawibel on 2010-08-08
I tried installing grub the way you said to, but it didn't work. The computer couldn't find grub. It said it might be in the wrong directory, I think. Is there another way? I'd still like to do this without installing grub if at all possible.

---

