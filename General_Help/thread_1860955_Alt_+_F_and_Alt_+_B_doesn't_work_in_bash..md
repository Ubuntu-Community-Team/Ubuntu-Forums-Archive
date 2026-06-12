---
title: "Alt + F and Alt + B doesn't work in bash."
date: 2011-10-15
forum: General Help
---

### Post by FKSP on 2011-10-15
Hi. Alt + F and Alt + B hotkeys doesn't work in my ubuntu 11.10 terminal (bash). Also the "View -> Show Menubar" option doesn't work.

How to fix it?

P.S.: If you find any mistakes, please, let me know, I'm working to improve my English.

---

### Post by mali2297 on 2011-10-15
Hello.

To troubleshoot...

Are 'alt+f' and 'alt+b' the only hotkeys that do not work? How about 'ctrl+b', 'alt+d' etc?

Do the hotkeys work in xterm?

Oh, and just to check, you do know that these hotkeys should move the cursor one word forward/back and nothing else, do you not?

---

### Post by FKSP on 2011-10-15
Yes, I know it. But when I press 'alt', I get access to a menu bar. Because:

"Menus in the menu bar can be accessed through shortcuts involving the Alt key and the mnemonic letter that appears underlined in the menu title."

So I can't use hotkey 'alt + <anything>'.

---

### Post by mali2297 on 2011-10-16
I do not use gnome-terminal, but how about checking the option "Disable all menu access keys"? (From [here]("http://library.gnome.org/users/gnome-terminal/stable/gnome-terminal-usage.html.en#gnome-terminal-shortcuts").)

Another alternative could be to use the Escape key. In that case, you need to press Esc+b in a sequence, not simultaneously as with Alt.

Yet another alternative is of course to use another terminal emulator.

---

