---
title: "[SOLVED] in fluxbox, apps aren't running from menu"
date: 2006-04-05
forum: General Help
---

### Post by antiemptyv on 2006-04-05
just some background--
I have been experimenting around with various window managers, and have decided that i prefer fluxbox to others, so on my laptop, i did a server reinstal, and apt-got fluxbox, added "exec startfluxbox" to my .xinitrc file, and fluxbox starts up fine with the "startx" command.

the real problem--
no applications are running from the menu, thought the menu, slit, and iconbar are all fully configurable.  the applications don't even attempt to run; a window doesn't even open for them.  apps that can run in a terminal run without problems before starting up X in the command line, such as Nano.

does anyone else know what's going on?

thanks.

---

### Post by taurus on 2006-04-05
Look in ~/.fluxbox/menu to make sure everything is good!!!

---

### Post by antiemptyv on 2006-04-05
thanks for the help, but i did think of this and everything looks fine.

anyone else?

---

### Post by croak77 on 2006-04-05
Did you make sure the apps are installed?

---

### Post by antiemptyv on 2006-04-05
yep, they are installed and the menu points to them correctly.  apps, such as Nano, run fine from the command line prior to logging into X, but running them from within fluxbox does nothing.

---

### Post by taurus on 2006-04-05
Then would you mind showing us what your ~/.fluxbox/menu look like then???

---

### Post by antiemptyv on 2006-04-05
sure.  i'm at work now, and i'll post it when it get home.  not that it necessarily matters, but i ran the same installation of fluxbox about an hour or so prior to reinstalling ubuntu on the system.  thanks for the help so far!

---

### Post by antiemptyv on 2006-04-05
well, not that i'm home, i realize that since i can't get any applications to run in fluxbox, i can't get on here to post my menu file.  hmmm...

---

### Post by antiemptyv on 2006-04-05
actually, the "restart," reconfigure," and "exit" menu commands work, so i'm confident things are set up correctly there.

---

### Post by antiemptyv on 2006-04-06
the only thing that i can think of (being not the most proficient linux user ever) is that something is not there to open the windows in which the programs appear.  everything looks just like my other fluxbox setup.  the only difference is that on this pc, i did a server install, and didn't install gnome, etc. that is installed by default with the regular install.

---

### Post by croak77 on 2006-04-06
Just to make clear, after doing the server install, you apt-get'ed any apps you wanted ie; firefox, xterm, xchat etc. Cause a server install doesn't install any by default.

---

### Post by taurus on 2006-04-06
[QUOTE=croak77]Just to make clear, after doing the server install, you apt-get'ed any apps you wanted ie; firefox, xterm, xchat etc. Cause a server install doesn't install any by default.[/QUOTE]
Yes, you have to install all those apps by hand if you picked the server option.  And if you have a fast internet, it shouldn't take too long and you only install apps that you want or use.  That would keep your system low in term of disk space.  ;)

---

### Post by barebones on 2006-04-06
How did you make your menu? Did you manually edit the ~/.fluxbox/menu file or did you use some other program? Can you get a terminal at all, once fluxbox is started? (I'm assuming not, since the menu isn't working) If not, add this line to your ~/.fluxbox/startup file, *before* the exec fluxbox command:
```
bash &
```
that should cause a terminal to open up when fluxbox starts. Try to start some stuff from there. That way we can narrow it down to a menu problem or a fluxbox in general problem.

---

### Post by antiemptyv on 2006-04-06
got it.  the problem with thhe terminal applications was that i didn't have x-terminal-emulator pointing to any terminal application, so none of those would open.

it's always easy to fix and hard to see.  just a quick *update-alternatives -config x-terminal-emulator* took care of it.

thanks for the help.

---

