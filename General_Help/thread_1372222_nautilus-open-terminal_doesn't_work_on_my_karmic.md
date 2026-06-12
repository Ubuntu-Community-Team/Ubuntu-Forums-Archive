---
title: "nautilus-open-terminal doesn't work on my karmic"
date: 2010-01-04
forum: General Help
---

### Post by garuhhh on 2010-01-04
nautilus-open-terminal doesn't seem to work on my ubuntu 9.10 (64bit). upon installation, it gives me the "Open in Terminal" shortcut in nautilus when i right-click, but doesn't give me the terminal.

But if i right-click in a nautilus with root privilege (gksu nautilus) the terminal shows upon choosing "Open in Terminal".

Thanks for any help!

---

### Post by mcduck on 2010-01-04
Make sure you have the default terminal application set.

I can't right now remember if the setting is anywhere in the menus, but you can definitely set it using Gconf Editor. Just press Alt-F2 and run "gconf-editor", browse to desktop/gnome/application/terminal and make sure the "exec"-key is set. (if it isn't, set it to "gnome-terminal", and the "exec_arg" to "-x".

edit. I just found it, the setting is is in System/Preferences/Preferred Application, under the "System"-tab.

---

### Post by garuhhh on 2010-01-04
yay! thanks mcduck! it now works!

although, it now shows the gnome-terminal. previously it uses xterm. Why do you think it stopped working?

EDIT: by the way, all keys are set, the only thing i changed is xterm (changed it to gnome-terminal) that's why it uses now the gnome-terminal.

---

### Post by ameno on 2010-02-04
im using "xfce4-terminal.wrapper" as default terminal, and the "open in terminal" plugin for nautilus also regressed with the upgrade from 9.04 to 9.10. (it did open a terminal window, but did not cd into the correct directoy, but stayed in ~)

solution for me was changing /desktop/gnome/applications/terminal/exec_arg from "-x" to "-e"

thx for the hint :)

---

### Post by P3t3r on 2010-05-02
Edit: never mind, I thought it didn't work but it seems I just had to restart nautilus. :-)

---

### Post by mc4man on 2010-05-02
> I just installed nautilus-open-terminal in Ubuntu 10.04, but I see nothing changed
restart nautilus or reboot - should show up

---

