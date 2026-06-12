---
title: "If screen goes black or unresponsive, how do i get out?"
date: 2010-10-25
forum: General Help
---

### Post by MollyWop on 2010-10-25
Sometimes if I'm doing something with wine, the screen will go blank or even unresponsive. What can I do to make it responsive and work again. I dont know the exact problem but does anyone know what I can do to fix this off the top of their head.

---

### Post by rajeevisonline on 2010-10-25
try to set a keyboard shortcut for system monitor by

gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_12 "gnome-system-monitor"
gconftool-2 --set --type string /apps/metacity/global_keybindings/run_command_12 "<Control><Alt>Delete"

when you get a black screen then try pressing ctrl-alt-del this should bring up system monitor or gnome-system-monitor from the command line.

is this doesnt work try something else..key is to setup a keyboard shortcut for system monitor...once you do that you can just use that shortcut to bring up system monitor and then end wine process..but you will lose all information in the windows process..wine is very temperemental it will either work very well..or not work at all..theyve really gotta fix it..i suggest u give crossover professional a serious though

---

### Post by NertSkull on 2010-10-25
it may not work, but you could also try alt+F2 and see if you can get to a terminal, then manually kill any process you need to, then restart the gdm

but maybe you can't get to a terminal when it locks up on you

---

### Post by sikander3786 on 2010-10-25
There is also a Ctrl + Alt + Backspace combination to kill the X server. It always works for me, just always.

Disabled by default, you can enable it from

System > Preferences > Keyboard > Layouts Tab > Options > Key sequence to kill the X server and tick the box.


Edit: Just note it is mighty powerful. It won't ask you anything before killing X and taking you to the login screen, you might lose all your un-saved data, Be cautious!

---

### Post by endotherm on 2010-10-25
> **NertSkull said:**
> it may not work, but you could also try alt+F2 and see if you can get to a terminal, then manually kill any process you need to, then restart the gdm

but maybe you can't get to a terminal when it locks up on you
or Ctrl + Alt + F1 to login to a vtty, and then use killall wine.

---

### Post by Jetso on 2010-10-25
In a terminal such as tty1, what is the command that is used to kill a certain program?

---

### Post by endotherm on 2010-10-25
> **Jetso said:**
> In a terminal such as tty1, what is the command that is used to kill a certain program?

well if you know the PID (you can find it from 'ps') you can kill a proc with 
```
sudo kill <pid number>
```
or if you just have the proc name you can kill all instances of that proc with :
```
sudo killall <proc name>
```

---

