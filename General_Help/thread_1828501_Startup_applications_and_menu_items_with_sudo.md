---
title: "Startup applications and menu items with sudo"
date: 2011-08-19
forum: General Help
---

### Post by creata.physics on 2011-08-19
So, bascially, any commands I enter into startup applications, will not work.

I recently installed XAMPP on a fresh ubuntu 11.04 install, and added the xampp start command to the startup applications, and it just does not work, it won't prompt me for my password, and it will not work.

The command I enter in the command text box is
sudo /opt/lampp/lampp start

It does nothing.

Also, I've installed bleachbit from the software center, and it added it's own menu item, which calls 'bleachbit' from the terminal, but when i modified the menu item, and made it sudo bleachbit, it no longer loads. No prompt for password, nada.

Any ideas on why this is happening?

---

### Post by CatKiller on 2011-08-19
Unless you run those applications in a terminal, there's nowhere to put your password. You can use gksudo instead, but you really shouldn't be running user applications as root. If there's something that you want started system-wide at boot there are better ways to do it.

---

### Post by creata.physics on 2011-08-19
Well, for things like XAMPP, bleachbit, and ddclient, what better way would that be?

They basically all need read/write permissions in /etc, /usr, /var, which you cannot do without root permissions, so like I said, what better way would there be for me to go about this?

---

### Post by mc4man on 2011-08-19
Anything you add to autostart is done thru a .desktop in ~/.config/autostart
You can add a new line to the .desktop(s) - 
```
Terminal=true
```
You may also want to stagger and delay them a bit, a line like this should do that, ex. 15 sec
```
X-GNOME-Autostart-Delay=15
```

---

### Post by creata.physics on 2011-08-20
Thank you very much you guys.  If a moderator could please changed this thread prefix to solved that would be great, thanks again.

---

