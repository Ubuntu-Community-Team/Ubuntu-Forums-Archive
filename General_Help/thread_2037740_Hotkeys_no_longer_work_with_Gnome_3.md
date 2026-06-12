---
title: "Hotkeys no longer work with Gnome 3"
date: 2012-08-05
forum: General Help
---

### Post by Starks on 2012-08-05
My volume hotkeys and launch terminal hotkeys are no longer responding even though xev is picking them up just fine.

Any suggestions?

---

### Post by cogier on 2012-08-05
I have also noticed this problem. I have been unable to fix it but a my work around is **[Super Key] > T > [Enter]** (Pressed one after the other not all together).

More testing has found a solution. Open the Keyboard app. Select the "Shortcuts" tab. Select "Launchers" in the left hand pane. Change the shortcut key sequence to something new e.g. [Ctrl] [Alt] R. (This is because I can't find a way to disable it). Then click on the "+" at the bottom of the window. This will bring up the "Custom shortcut" menu. For name type "Gnome Terminal" (or whatever you like) for command enter "gnome-terminal" and click "Apply". In the right window click on the "Disabled" word in the "Gnome Terminal" line and enter [Ctrl] [Alt] T. Then test it out.

---

### Post by Starks on 2012-08-05
That's what I've done in the past, the custom keybindings don't work once these symptoms appear.

---

