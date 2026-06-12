---
title: "Keyboard Control &amp; XMMS"
date: 2006-03-31
forum: General Help
---

### Post by th3gh05t on 2006-03-31
Hi, 

I have tried to edit the 'Keyboard Shortcuts' in the 'System > Preferences > Keyboard Shortcuts', but I can't get it to work. (In fact, I messed the keyboard and how it should work.)

Is there an easy way to set keyboard commands for Play, Pause, Volume, etc.?

Thanks for your help!

*th3gh05t*

---

### Post by NeghVar on 2006-03-31
For me volume worked out of the box, but so far with the others its been no good.

---

### Post by th3gh05t on 2006-04-04
Dos anyone have any insight into this issue?

---

### Post by IYY on 2006-04-04
If you plan to use Gnome's keybinding editor, I don't think you'll be able to control XMMS. It only controls Gnome's default player, Rhythmbox. I don't use Gnome right now, but I know that to control XMMS, we need to run commands like "xmms -u" to pause and "xmms -p" to play. "man xmms" to get the full list of commands.

How to make Gnome execute a terminal command with keybindings? Run the Gnome configuration editor (gconf-editor in the command line) and go to apps > metacity > global_keybindings. There are fields there named "run_command_n" with n being some number. You enter your keyboard shortcuts here, and then go to apps > metacity > keybinding_commands and set the commands. For example, command_1 could be "xmms -u" and command_2 could be "xmms -p".

---

### Post by mattalves on 2006-12-06
Other commands for xmms are:

-p  > play
-u  > pause
-f  > next track
-r  > previous track
-s  > stop 
-t  > play/pause

---

### Post by stylishpants on 2006-12-07
The problem is xmms.  It's an old player and by default it doesn't know how to recognize the standard XF86 multimedia keys.  It is not true that those keys only work with rhythmbox by default.  They should also work automatically with amarok, quodlibet, and others.

To make this work with xmms, just install this package: xmms-xf86audio

---

