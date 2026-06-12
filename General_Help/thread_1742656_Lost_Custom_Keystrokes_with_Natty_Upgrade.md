---
title: "Lost Custom Keystrokes with Natty Upgrade"
date: 2011-04-29
forum: General Help
---

### Post by gregalynch on 2011-04-29
I have a script that toggles my touchpad on and off and I assigned it a custom keystroke using gconf-editor.  It worked fine until I upgraded to Natty and now I can't make it work anymore.  I checked and the script is still the value of 'command_1' and the same keystroke (<Alt>t) is still the value of run_command_1 in the universal keybindings.  But, for whatever reason, when I hit <Alt>t, nothing happens.  I've tried using assigning different keystrokes, but nothing has worked.

---

### Post by Shekibobo on 2011-04-29
I'm having a similar problem with the "Run a terminal" command set to Ctrl+Alt+Space, and it doesn't work anymore. Actually it works find when I'm using Unity (which after being completely unable to resize that grossly huge launcher bar), but when I'm using "Classic Ubuntu," the shortcut doesn't work.

Edit: workaround => run 'gnome-terminal' with key bindings.  Apparently the 'Run a terminal' is obsolete.

---

### Post by gregalynch on 2011-04-29
I've played around a little more and it seems that the problem is somewhere in gconf.  All of the standard keyboard shortcuts work, but none of the user-defined ones do.  Its not just my toggle script that doesn't work, I can't get any commands to run with a keystroke assigned to them.  Its almost like there's a miscommunication somewhere between the 'keybinding_commands' section, where you assign a command to 'command_1' or 'command_2' and the 'global_keybindings' section where you assign a keystroke to the command.  That would explain why your user-defined terminal command isn't working, either.

I don't know a ton about computers, so I can't say any more than that.

---

### Post by gregalynch on 2011-04-29
Aha.  I just saw that there's a way to assign shortcuts under system-> preferences -> keyboard shortcuts.  I assigned it using that instead of gconf-editor and now it works.

---

