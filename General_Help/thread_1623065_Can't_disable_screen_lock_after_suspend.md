---
title: "Can't disable screen lock after suspend ??"
date: 2010-11-16
forum: General Help
---

### Post by fictivetoast on 2010-11-16
I recently upgraded from Lucid to Maverick I can't seem to disable screen lock after resume from suspend.  It's a minor annoyance, but still a considerable annoyance to have to enter my password every time the computer wakes up.

I've thusfar 

1 - changed screensaver preferences to not lock

2 - set the **gnome_keyring_hibernate**, **gnome_keyring_suspend**, **hibernate**, and **suspend**, values all to false in gconf-editor

3 - commented out the line **LOCK_SCREEN=true** in /etc/default/acpi-support

BUT am still being prompted for a password every time the computer wakes up from suspend.  I'm stumped, what could I be forgetting?

Thanks in advance for any advice.

---

### Post by Quackers on 2010-11-16
Hit Alt+F2, or if that doesn't work (like mine) open a terminal and type gconf-editor and hit enter. The gconf editor will appear with 4 options on the left. Click on the down arrow next to Apps, then scroll to Gnome Power Manager and click on the down arrow again. Double click on Lock and on the right side of the screen make sure use_screensaver_settings box is checked. If it is checked try unchecking then re-checking it, then quit the editor.

---

### Post by fictivetoast on 2010-11-17
Have double checked and reset all the gnome-power-manager settings in gconf-editor, to no avail.  Any other ideas ?

---

### Post by fictivetoast on 2010-11-20
Sorry to bump, but does anyone else have any insight?

---

### Post by benoliver999 on 2011-04-21
Hate to be annoying, but I'd quite like to know the answer too - I'm on Natty now.

---

### Post by benoliver999 on 2011-04-21
Sussed it - I was opening gconf-editor with sudo, when I should have done it without.

In terminal, just type ```
gconf-editor
``` WITHOUT sudo in front, then see if the settings are unchecked there. I think it's under apps>gnome-power-manager>lock

Did the trick for me, hope this helps.

---

### Post by justinjstark on 2011-07-12
I have done the following:

1) gconf-editor
2) Uncheck all in apps/gnome-power-manager/lock
3) Check use_screensaver_settings
4) sudo gconf-editor
5) Repeat 2 & 3
6) Comment out LOCK_SCREEN=true in /etc/default/acpi_support
7) Restarted

I still get a password prompt after suspend.  Help.

---

### Post by psusi on 2011-07-12
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/578542](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/578542)

---

### Post by benoliver999 on 2011-07-13
I also have, in gconf-editor (still without sudo), desktop>gnome>lockdown>disable_lock_screen checked. Give that a go.

---

