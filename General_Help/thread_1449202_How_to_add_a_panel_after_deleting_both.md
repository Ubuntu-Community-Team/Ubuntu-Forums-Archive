---
title: "How to add a panel after deleting both?"
date: 2010-04-07
forum: General Help
---

### Post by arnab_das on 2010-04-07
Say, i have deleted both the panels of ubuntu (the top and the bottom one). how do i now add panels?

actually, i only know about adding panels by right clicking "Add panel" on the existing ones.

---

### Post by gemmakaru on 2010-04-07
I really wish I knew to the answer to this, I really do.  It could happen to anyone.  You could always create launchers for your apps?  Maybe you could find a way to create a launcher for the add panels screen.  *Awaits expert.

---

### Post by J V on 2010-04-07
Deleting your config files should do the trick (/there are lots of threads on this, use search)

---

### Post by Ric_NYC on 2010-04-07
That happened to me a few times. The same issue in KDE and Gnome.

Deleting panels (the default) should not be an option.

---

### Post by Phrea on 2010-04-07
[http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/](http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/)

---

### Post by Psumi on 2010-04-07
> **Ric_NYC said:**
> That happened to me a few times. The same issue in KDE and Gnome.

Deleting panels (the default) should not be an option.

GNOME doesn't allow you to delete the last panel, nor XFCE. Delete Panel is usually grayed out.

---

### Post by sisco311 on 2010-04-07
to restore the default panels, run:
```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

---

### Post by Psumi on 2010-04-07
> **sisco311 said:**
> to restore the default panels, run:
```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

GNOME Panel is the application that provides the Run Dialog. Deleting both panels removes the run dialog capabilities.

If you don't have a filesystem link on your desktop nor a link to terminal nor the nautilus-open-terminal plugin, nor a dock,

you force the user to do TTY1 (CRTL+ALT+F1.)

---

### Post by Ric_NYC on 2010-04-07
> **Psumi said:**
> GNOME doesn't allow you to delete the last panel, nor XFCE. Delete Panel is usually grayed out.

Oops... My mistake. Thanks for the info. That's the way it should be.

---

### Post by kristine12 on 2010-04-07
Try using this command in terminal:

This will shutdown curently running gconf editing daemon (**gconfd** service) temperorly for the user.
```
gconftool-2 --shutdown
```

This will get rid of your current panel for your username only from your home
```
rm -rf ~/.gconf/apps/panel
```

This will kill(stop) all currently running panels for your user account
```
pkill gnome-panel
```

Logout and log back in again.
Once you log back in again, panels will be recreated and restored to default settings.

That's all!
All credits to '**ukripper**'.

---

### Post by Psumi on 2010-04-07
> **kristine12 said:**
> Try using this command in terminal:

Read Post #8

In addition, what if the user doesn't know that password entries don't show asterisks, and doesn't move the cursor? The user will be furious and think they aren't typing the password at all.

---

### Post by sisco311 on 2010-04-07
> **Psumi said:**
> GNOME Panel is the application that provides the Run Dialog. Deleting both panels removes the run dialog capabilities.

If you don't have a filesystem link on your desktop nor a link to terminal nor the nautilus-open-terminal plugin, nor a dock,

you force the user to do TTY1 (CRTL+ALT+F1.)

Good point!

@OP

You can create a launcher for a terminal. Right click on the desktop & select *Create Launcher...*. In the Command field type *gnome-terminal*, in the Name filed *terminal* (or whatever you want) & click the OK button. Then simply double click the launcher to start the terminal.

---

### Post by arnab_das on 2010-04-07
thank you! :) that was immensely helpful! one cant delete the final panel. thats what i just found out. great!

---

### Post by cariboo on 2010-04-07
Not a Cafe thread moved to General Help

---

