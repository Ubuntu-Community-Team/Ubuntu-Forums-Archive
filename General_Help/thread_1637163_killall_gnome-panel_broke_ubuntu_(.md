---
title: "killall gnome-panel: broke ubuntu :("
date: 2010-12-04
forum: General Help
---

### Post by Prium on 2010-12-04
Regarding the gnome-panel in Ubuntu (64 bit)....

I discovered some time ago that I wasn't the only one who routinely (every login) had their gnome-panel appear butchered, for which Alt-F2 then 'killall gnome-panel' would easily fix. 

Having become impatient with this over the past 8 months, I decided I would automate the process and so cofiguring the startup applications seemed like a perfectly logical choice to me. Turns out I was wrong. After adding 'killall gnome-panel' to the startup applications not only does the panel fail to load altogether now, but Alt-F2 doesn't even work. 

I tried Ctl-Alt-F1 and working with the graphics-free mode thinking I could somehow navigate to the startup apps config file and edit it, but I don't know where it is or how to edit it without logging in as root and I certainly don't know of any 'root password'.

Any suggestions?

---

### Post by karthick87 on 2010-12-04
Try the folowing,
```

gnome-session-remove gnome-panel
```
```
gconftool-2 --recursive-unset /apps/panel
```
```
gnome-panel &
```

---

### Post by Prium on 2010-12-04
Thanks for your reply. I tried what you suggested (Ctl-Alt-F1) and these are what it returned: 


> **karthick87 said:**
> Try the folowing,
```

gnome-session-remove gnome-panel
```

"command not found"

```
gconftool-2 --recursive-unset /apps/panel
```

"Error while parsing options: Unknown option --recursive"

```
gnome-panel &
```

"Gtk - Warning **: cannot open display"

---

### Post by karthick87 on 2010-12-04
Press CTRL+ALT+F7 and then excute those commands in your terminal.

---

### Post by wojox on 2010-12-04
Remove killall gnome panel from Start up and run these three commands and restart:

```
sudo gconftool-2 --shutdown
sudo rm -rf .gconf/apps/panel
sudo pkill gnome-panel

```

---

### Post by Prium on 2010-12-04
> **karthick87 said:**
> Press CTRL+ALT+F7 and then excute those commands in your terminal.

CTRL-ALT-F7 does not bring up the terminal. 

CTRL-ALT-F2 isn't helping either. 

If I had a way to get to the terminal once the graphical session has started I should be fine. But the only access to the terminal I can find is going CTRL-ALT-F1/2/3/4 and I have had no luck so far (see error messages to your previous suggestions).

---

### Post by 0949er on 2010-12-04
at the login, (in ctrl+alt+f1) you need to log in as your default users, and then run "sudo" IF you actually need root privileges to remove/edit that startup file.

---

### Post by Prium on 2010-12-04
> **0949er said:**
> at the login, (in ctrl+alt+f1) you need to log in as your default users, and then run "sudo" IF you actually need root privileges to remove/edit that startup file.

Perfect!

I ended up using Midnight Commander to locate and edit ~/.config/autostart and all I had to do was to delete the offending entry 'killall gnome-panel'

Thanks everyone for all of your suggestions :)

---

### Post by karthick87 on 2010-12-04
Mark your thread as [SOLVED]

---

### Post by Prium on 2010-12-04
> **karthick87 said:**
> Mark your thread as [SOLVED]

Umm, thanks yeah I did, right after I solved it ;)

---

