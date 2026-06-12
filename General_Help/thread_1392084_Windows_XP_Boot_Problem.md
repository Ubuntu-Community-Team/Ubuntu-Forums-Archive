---
title: "Windows XP Boot Problem"
date: 2010-01-27
forum: General Help
---

### Post by mut4nt on 2010-01-27
Ok so, I did a fresh install of Windows Xp Pro on my aunts computer for her, everything went smooth, although when booting it gives the option for booting Windows Xp Pro, Windows Xp Home, and antoher Windows Xp Home, those xp homes do not exist, I formatted & deleted the other partions when I did the fresh install, whats the deal? I couldnt figure out how to put together a phrase to google for this so I figured Id just post here. Thanks for the help!~

---

### Post by Lundis500 on 2010-01-27
In command-line you can type this: fixmbr
maybe also fixboot 
If windows refuses to do that, boot with the XP CD and start the recovery console, then run the commands.

---

### Post by J V on 2010-01-27
it probably left the mbr behind... I guess...

You can edit the boot options to get rid of the menu in the config panel (power settings I think?)

---

### Post by mut4nt on 2010-01-27
worked :) thanksss

---

