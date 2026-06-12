---
title: "Unable to unbind ALT+~ since 11.10."
date: 2011-10-13
forum: General Help
---

### Post by nezkun on 2011-10-13
I used to use ALT+tilde to switch to the terminal prior to 11.10 (I used Guake). Since the upgrade I cannot use this shortcut, as it appears to now have a system function similar to alt+tab.

Is there any way around this?

---

### Post by nezkun on 2011-10-13
Created custom shortcut in system settings->keyboard that seemed to override the new feature. I guess this can be resolved.

---

### Post by akudlick on 2011-10-17
Could you explain what you did? I use alt-tilde as a hotkey in intellij, so I want to disable the ubuntu hotkey, not map it to another.  Would that be possible with your solution?

---

### Post by cbmanica on 2012-02-17
After 20 minutes of pure pain, I can report that the suggestion to use custom keybindings to "fix" the alt-tilde keybinding not only doesn't work, it exposes the fact that custom keybindings is itself horrendously broken.  Want to see the fun?  Create a random command, map a keybinding to it (one you DON'T care about), and then delete the command.  WOOHOO your custom keybinding is STILL BOUND with no apparent way to EVER change it!

(If you tried this solution and trashed your keybindings, try creating two bogus commands, and assign the keybinding you want back to both of them, which seems to force the UI to revoke any previous bindings, and then unmap it from the commands you can actually see.  All I know is that worked for me.  If someone knows which voodoo config file actually stores this nonsense, obviously that's a much more direct way to deal with the keybindings.)

**ACTUAL SOLUTION TO ALT-TILDE PROBLEM: **(at least that which worked for me) [http://ubuntuforums.org/showthread.php?p=11695344](http://ubuntuforums.org/showthread.php?p=11695344)  Hope that helps someone.

---

