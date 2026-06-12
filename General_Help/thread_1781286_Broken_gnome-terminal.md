---
title: "Broken gnome-terminal"
date: 2011-06-13
forum: General Help
---

### Post by Howy on 2011-06-13
I'm a big fan of using the terminal, which is why I have an own, simple shortcut on the keyboard for it. The terminal looks good and I love it.
However... There is trouble in wonderland.
When I try to open gnome-terminal, I get this error:
```
There was an error creating child process for this terminal

grantpt failed: Invalid executable file format
```
I've checked gnome-terminal, bash and all the other shells. They're all intact and nothing is wrong with them.
I've tried reinstalling, but it doesn't seem to have an effect.
In the settings, an option named: "Update log entries when the command is started" is enabled. "Run command as login shell" and "Run custom command instead of shell" are disabled. I hope it helps.
Till then... I'm stuck with the old xterm... :neutral:

And for the record, I've made a full backup of my system, with every single configuration file, before this occurred. So just tell me which file it is, and I can restore it to a working state.

---

### Post by Yellow Pasque on 2011-06-13
This was all I could find: [https://bugzilla.redhat.com/show_bug.cgi?id=509632](https://bugzilla.redhat.com/show_bug.cgi?id=509632)

---

### Post by MooPi on 2011-06-13
Are still using the shortcut icon ? Try to start from alternate source. Open xterm and type ```
gnome-terminal
``` Or ```
Ctrl + F2
```

---

### Post by Howy on 2011-06-13
I tried both through Alt+F2 and Xterm, but they turned out the same.

This command fixed it:
```
mount -o remount,mode=620 /dev/pts
```
The bug report gave the solution, so thanks. :)

---

