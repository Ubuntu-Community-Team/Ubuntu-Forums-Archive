---
title: "Making xrandr settings permanent"
date: 2009-09-16
forum: General Help
---

### Post by Blue Rose on 2009-09-16
Hey all,

I just installed Ubuntu on my laptop, a Packard Bell MH36 something.
Everything works just fine except one very odd thing:
The screen resolution is set to 1024*768 for both the login screen and the desktop, whereas my laptop has a 15" 1280*800 screen. This leaves me with a small square screen in the middle, and two thick black bars at the sides.

First I thought maybe it was Kubuntu, so I installed Ubuntu but the same problem persists.

I tried the desktop/screen settings applet, it sees two monitors, the 15" screen and a TV. the TV would be the VGAoutput. I cannot disable it in the applet. The problem seems to be that (k)Ubuntu sets the VGA/TV (which is not connected) as the primary monitor, and thus chooses the wrong resolution.

In kubuntu just opening the applet was enough for the laptop to realize it should set itself to 1280*800, which of course is weird already that a setting would change by just loading a settings panel.
In gnome I can set the proper resolution in the screen applet as well. But the setting is not permanent.

What I do now is set xrandr --output TV off in the terminal, which works like a charm, but again does not persist after a reboot.

What I need to know now is how to make it permanent?? It's getting really annoying to have to do this at every reboot. >.<

Any other solutions are welcome as well, but I do not need the VGA output, so I don't mind switching it off permanently.

I will gladly give more information if needed, just let me know.

Thanks in advance
Linda

---

### Post by quixote on 2009-09-17
One simple workaround is to put the command in your .bashrc.  This is a file of commands that you want to run on bootup.  There's usually a default one already in your home directory.  It's a hidden file, so "show hidden files" to see it.

If there isn't one, just use a text editor like gedit to save a file with that name.

Commented lines with a # are not run.  Everything else is a command, so be sure it's what you want.  For example:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples
xrandr --output TV off
``` (Or whatever the proper xrandr command would be)

---

### Post by Blue Rose on 2009-09-17
Thank you! :D I will try this right away, but it looks like the thing I was looking for ^_^

---

