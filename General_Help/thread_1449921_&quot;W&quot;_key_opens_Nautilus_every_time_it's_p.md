---
title: "&quot;W&quot; key opens Nautilus every time it's pressed?"
date: 2010-04-08
forum: General Help
---

### Post by paraplegicpanda on 2010-04-08
Okay, so I turned on my box this morning and went straight into WoW. Strangely, and just this morning, a shortcut function seems to have been added to my "W" key that makes it open up Nautilus every time it is pressed. I've checked in both "System > Preferences > Keyboard" and "System > Preferences > Keyboard Shortcuts and I can't find anything showing that it should be doing this. Any help would be greatly appreciated in removing this shortcut. Thanks!


Ubuntu 9.10 Karmic Koala

---

### Post by Greenwidth on 2010-04-08
Run gconf-editor and have a look in:
apps > metacity > global_keybindings
might be in there.

---

### Post by paraplegicpanda on 2010-04-08
Unfortunately it's not. I've also checked in desktop > gnome > keybindings in gconf but I can't seem to find anything so far.

---

### Post by rahilm on 2010-04-08
if you are running compiz and have installed compiz config settings manager, open it and check the first plugin "Commands".. might be there

---

### Post by paraplegicpanda on 2010-04-08
Nope, I was actually looking through that in gconf, but it was easier to look through in the GUI. Still, no luck so far.

---

### Post by paraplegicpanda on 2010-04-08
Bump. This is seriously making it incredibly difficult to use my computer.

---

### Post by paraplegicpanda on 2010-04-09
Bump, I'm still trying to figure this out. Any suggestions AT ALL... ?

---

### Post by cogier on 2010-04-09
Can you define "W" to shortcut to something else (e.g. Firefox or F-Spot). If you can you might be able to set up a script to get it to work as "W".

---

### Post by paraplegicpanda on 2010-04-09
Okay, I've finally found the problem. The multimedia keys report themselves as "X86EXPLORER" or "X86WWW" to applications. When I tried using Commands in Compiz it would capture the key as a "w" most of the time but every once in a while it would capture it as "X86EXPLORER" which is set to open Nautilus. Now that I disabled that key in "System > Preferences > Keyboard Shortcuts" I'm no longer having trouble. Thanks all!

---

