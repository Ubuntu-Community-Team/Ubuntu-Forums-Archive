---
title: "Help with xsendkeys"
date: 2011-04-13
forum: General Help
---

### Post by ksandifer on 2011-04-13
I've been searching for a while now but can't find what I'm looking for.  I want to make a keyboard shortcut that runs a script that types keystrokes wherever the cursor is.  For example, if I am in a text editor and press "ctrl+alt+q", I would like it to type some predetermined string to the page.  On Windows, AutoHotKey does this.  I can't seem to get it working in gnome, though.

I have installed lineakd, and I have a file ~/.scripts/type.sh that looks like:

#!/bin/sh
xsendkeys "blahblahblah"

I have the command
sh ~/.scripts/type.sh
set to the key combination I want in system->preferences->keyboard-shortcuts.

I'm sure I'm not using xsendkeys correctly, but couldn't find much documentation on it. Anybody know how xsendkeys works or how I might solve this problem another way?

---

### Post by ksandifer on 2011-04-13
shameless self bump

---

### Post by ksandifer on 2011-04-13
So this is like a bump and an update at the same time. I found the "xte" command.  'xte "key k"' is in type.sh and will print the letter k ONLY if i run "~/.scripts/type.sh" in a terminal.  It prints the letter at the command line. I still can't get it to print into a text editor or anything though.


EDIT: solved my own problem. Just in case anyone wants to know in the future, I used the "xsendkeycode" command about 40 million times. The script file looks like:

#!/bin/sh
sleep 0.5
xsendkeycode (keycode) 1
xsendkeycode (keycode) 0
...

Also, I used CompizConfig Settings Manager to set the shortcut keys instead of the keyboard shortcuts thing.

---

