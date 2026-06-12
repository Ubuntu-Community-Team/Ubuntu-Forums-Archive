---
title: "No menu bar"
date: 2010-05-04
forum: General Help
---

### Post by seubill on 2010-05-04
Upgraded to 10.04 from 9.10, now the menu bar is missing. Can't open "add to panel" with right click.


Appreciate the help, thanks!

---

### Post by WorMzy on 2010-05-04
Try resetting the panels. In a terminal write:

```
mkdir ~/.oldpanel
```then
```
mv ~/.gconf/apps/panel ~/.oldpanel
```then
```
*gconftool-2 --shutdown*
```finally
```
pkill gnome-panel
```

NOTE: This will completely reset your panels to the default configuration, they will look the same as if you'd done a fresh install.

---

### Post by seubill on 2010-05-04
WorMzy. followed your instruction but nothing changed. I'm getting this message when I reboot: "The panel encountered a problem while loading "OAFIID:GNOME_GoHome".

---

### Post by WorMzy on 2010-05-04
Are you sure you performed all the instructions correctly? GNOME_GoHome doesn't seem to be a default applet, so it shouldn't show up after resetting the panels..

Can you run gconf-editor and browse to /apps/panel/applets/ and look through all the subfolders for the one with that bonobo_iid. Make a note of the subfolders name, then run:
```
rm ~/.gconf/apps/panel/applets/<Subfolders name>
```

---

### Post by seubill on 2010-05-05
its applet_0, and its locked. the rm command didn't do anything.

---

### Post by WorMzy on 2010-05-05
Sorry, that should have been```
rm _-r_ ~/.gconf/apps/panel/applets/<Subfolders name>
```

Try that, then re-run the bottom two commands from my original post.

---

### Post by seubill on 2010-05-05
This is very stubborn.  Reran the command  with the -r and your two last commands from before.  Nothing has changed and on reboot the same error message appears. Checked in gconf-editor and applet_0 is still there.

---

### Post by WorMzy on 2010-05-05
I am flummoxed. That should have worked as I tested it on my own machine. :S

Run 'ls ~/.gconf/apps/panel/applets' in a terminal, is applet_0 still there?

---

### Post by seubill on 2010-05-05
I can't say with the ls command. I am having to use Alt+F2 to run the command and then it flashes by so fast that its impossible to read. How else can I open terminal? I don't have a menu bar to open and then select terminal.

---

### Post by WorMzy on 2010-05-05
Ah! I'm sorry, I should have realised you would be using the run command for everything. Run 'gnome-terminal', and try my first post again.

---

### Post by seubill on 2010-05-05
Okay. at least I know how to open terminal in this state. Ran all the commands from your first post in terminal, and then rebooted. No change resulted, same error message box, but the date and time applet at the top was faded out. No way to right click and open "add to panel" to get me a menu bar. Ran the ls command and applet_0 did not show in the output. Ran gconf-editor and sure enough, applet_0 is still inplace.

---

### Post by WorMzy on 2010-05-05
The only other thing I can think of is to remove your .gconf and .gconfd folders to force a _complete reset_ all your gnome settings to the defaults. I don't know if this will help, and it will mean that you will lose any configuration changes you have made since you installed Ubuntu. For this reason, the first part of the following command only renames the folder, rather than deleting it, so you can revert the changes if necessary.

```
mv ~/.gconf ~/.gconf.old && rm -rf ~/.gconfd && gconftool-2 --shutdown && pkill gnome-panel
```

If that fails, then I truly am out of ideas.

---

