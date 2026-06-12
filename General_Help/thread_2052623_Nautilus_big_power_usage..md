---
title: "Nautilus big power usage."
date: 2012-09-03
forum: General Help
---

### Post by tomatoe on 2012-09-03
Hello!

Right now I'm watching my System monitor's Processes tab and I found out that one of the top CPU usage goes to Nautilus, although Nautilus  is not currently opened.  It is Nautilus -n when I move mouse over it in System Monitor. 

I did

```
nautilus -h
Usage:
  nautilus [OPTION...] [URI...] 

Browse the file system with the file manager

Help Options:
  -h, --help                  Show help options
  --help-all                  Show all help options
  --help-gtk                  Show GTK+ Options

Application Options:
  -c, --check                 Perform a quick set of self-check tests.
  --version                   Show the version of the program.
  -g, --geometry=GEOMETRY     Create the initial window with the given geometry.
 ** -n, --no-default-window     Only create windows for explicitly specified URIs.**
  --no-desktop                Do not manage the desktop (ignore the preference set in the preferences dialog).
  -q, --quit                  Quit Nautilus.
  --display=DISPLAY           X display to use

```What is that thing and should it be so normally?

Thanks!

---

