---
title: "Running X without WM or DE"
date: 2009-12-04
forum: General Help
---

### Post by lewisforlife on 2009-12-04
I am working on a POS system for a school project.  I want to load my program on Ubuntu startup without loading a Windows Manger or Desktop Environment (this is not part of the school project, I just want to do it to learn).  What is the best way of doing this.  I have tried with a DE, twm, but don't really want to use a DE.

I know that I want a bash script to run on startup to load my graphical program, but am not sure what X stuff I need in the bash script to load a graphical program if there is not WE or DE.  The reason I want to do this, is I want the user to only see the POS system, and not the desktop.  Any help would be much appreciated, thanks.

---

### Post by falconindy on 2009-12-04
Boot to a text login and create a file called .xinitrc in your home directory. In it, put the following:

```
exec xterm
```

Save it, make sure its executable, and run `startx`. That runs the X server with only xterm. If you're running more than 1 window, I'm fairly sure you're going to want SOME kind of window management. DWM might suit your needs as its insanely small and provides only a basic framework for managing (resizing/moving) windows.

---

### Post by lykwydchykyn on 2009-12-04
I'll second falconindy; you'll want some kind of window manager.  I make kiosks often, and I've found matchbox window manager is ideal for this sort of situation.

You can run without a window manager, but your biggest issues will be
 - making windows full-screen
 - dealing with pop-up windows (errors, config dialogs, etc).

Of course, try it both ways, it may be your app runs fine without a wm.


check out this page: [https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

---

### Post by lewisforlife on 2009-12-04
Thanks for the suggestions, I will look into some windows managers.  How do I tell Ubuntu to boot to a text login instead of the graphical login?

---

### Post by MaxIBoy on 2009-12-04
Well, you can switch to a virtual terminal by hitting ctrl-alt-F[number between 1 and 6] to switch between them (virtual terminal 7 is your x session,) but of course the X session is still running.


Booting to recovery mode will give you a textmode, but it won't be a complete system.


What I did is I installed a program called sysv-rc-conf. Install it, pull up a terminal, and run it with sudo. There you can enable and disable different programs for each runlevel. For runlevel 3, you can disable GDM/KDM/XDM/whatever display manager you use. Then, you can choose to boot runlevel 3 by adding a grub menu entry and adding "3" to the line of that entry. If you choose that entry in the grub menu, you can then boot to runelvel 3 and it will be a complete text mode.

If you want textmode by default, disable your display manager in runlevel 2 (the default,) and to start it you can run sudo /etc/init.d/gdm start.

---

### Post by falconindy on 2009-12-04
Append 'text' to your kernel options in GRUB.

---

### Post by lykwydchykyn on 2009-12-04
You can uninstall gdm, or use the following command:

```

sudo update-rc.d -f gdm disable

```

---

