---
title: "PATH variable in root terminal"
date: 2010-03-16
forum: General Help
---

### Post by Axel van Moorsel on 2010-03-16
I want to add a path (/usr/sys) to the global $PATH. I will use this to test commands and scripts, which I don't want to be mixed up with regular commands.
I've added the path to /etc/environment. When I start a terminal session under my user account, the path is included in the $PATH variable. However, when I start a root terminal, it is not.

Is there a way to to change $PATH on  one place where it will also affect the root terminal, or do I have to change it on 2 locations?

---

### Post by Brandon Williams on 2010-03-16
If I modify the path in /etc/environment, open a shell, and run 'sudo -i', the changes that I have made are applied to my root login shell. What are you doing to 'open a root terminal'? If it's from a menu option, what is the specific command that is run? It may be that the command is not giving you a login shell (i.e. it's running the equivalent of 'sudo -s' instead of 'sudo -i') and it may be that your change to the path is not present in the environment for your graphical session; only for a terminal.

Try adding the PATH change to your own .profile, or explicitly source /etc/environment from your .profile. The gdm Xsession will source your .profile for you, so if you modify the PATH in your .profile, it will have an impact throughout your environment.

---

### Post by Axel van Moorsel on 2010-03-16
Thanks. It doesn't quite answer my question, but it does solve my problem in an other way.

I am new to Linux. I didn't know the option "sudo -i" (as a matter of fact, I only know few options), but this seems to serve the same purpose as the "root terminal".

The root terminal is an option I came across when looking through options that could be added to the menu. It seemed useful, because it made possible to do stuff from the prompt without having to provide a password each time.

I don't know what command is used when I use this menu item, since I haven't figured out yet how to add my own items to the standard menu, nor how I can see the properties of the preconfigured menu items.

I made changes to my .profile, but this didn't have any effect on the "root terminal".

---

### Post by Brandon Williams on 2010-03-16
Did you log out and log back in after making the changes to your .profile? That would be required in order to update the path setting in your graphical login environment. If that's not enough to solve the problem, then read on for another approach ...

Are you using the standard Ubuntu desktop environment (Gnome)? If so, then there should be a menu entry under Preferences titled 'Main Menu'. Open that app and find the entry for 'Root Terminal'. The command will be 'gksu /usr/bin/x-terminal-emulator', I think. Try changing the command to 'gksu /usr/bin/x-terminal-emulator -e bash -l' so that it will run bash as a login shell within the root terminal. That should result in /etc/environment being applied. You will also need to add the following line to /root/.profile:
```
. /etc/environment
```

---

### Post by Axel van Moorsel on 2010-03-17
Logging out and back in is almost standard for me when things don't work after changing settings in profiles etc.

I've changed the command that starts the root terminal, but after that the root terminal wouldn't start at all (or maybe the process started, but I didn't get the terminal or an icon in the menu bar. Added the . /etc/environment to the root .profile: didn't help, not even after rebooting the computer (maybe a little drastical, but then I know for sure that changes should have been applied and functional.

Changed the command that starts the root terminal back to its original form, while keeping the change to the root .profile. Root terminal did start, but $PATH was still in it's original form, without my addition.

The sudo -i option works perfect and gives me all the functionality I need for now, so I will close this thread.

Thank you very much for your support.

---

