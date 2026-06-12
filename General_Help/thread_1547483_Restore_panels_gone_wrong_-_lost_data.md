---
title: "Restore panels gone wrong - lost data"
date: 2010-08-06
forum: General Help
---

### Post by Azgaroth on 2010-08-06
Hi guys and gals.
I have tried to restore my panels to their default settings via this couple of lines:

gconftool-2 –shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

It fixed my panels but lost my files in the home folder. All my programs are still installed but lost their settings and data.
Is there anything that can be done?

Thanks in advance

---

### Post by WorMzy on 2010-08-06
That command doesn't touch any folder in your home directory except ~/.gconf/apps/panel; if you've lost any files it's due to something else. Can you post the last few lines of ~/.bash_history?

---

### Post by Azgaroth on 2010-08-06
1  gconftool-2 – -shutdown
    2  gconftool-2 –shutdown
    3  gconftool – -recursive-unset /apps/panel 
    4  gconftool-2 -shutdown
    5  gconftool-2 --shutdown
    6  gconftool – -recursive-unset /apps/panel
    7  pkill gnome-panel
    8  rm -rf ~ /.gconf/apps/panel
    9  mkdir ~/.oldpanel
   10  mv ~/.gconf/apps/panel ~/.oldpanel
   11  gconftool-2 --shutdown
   12  pkill gnome-panel
   13  gconftool-2 --shutdown
   14  rm -rf ~/.gconf/apps/panel
   15  pkill gnome-panel
   16  mv ~/.gconf/apps/panel ~/.oldpanel

Guess that's all. Hope is enough though.

---

### Post by WorMzy on 2010-08-06
There's your offending command:
> 8 rm -rf ~ /.gconf/apps/panel
(Note the space between the ~ and first slash)

That'd remove everything in your home folder, then anything in "/.gconf/apps/panel" (which doesn't exist).

Don't play around with commands like that, especially not rm -rf commands. rm = remove, r = recursive, f = force. rm -rf will remove anything, without asking for confirmation, and should only be used when you know what you're doing. The things it removes are not easily recoverable.

I'm afraid that the only realistic solution for you is to create a new account, then either use that account, or copy over all it's contents to your first account's home folder. If you lost important documents/media, then you're going to have to use to a data recovery application (such as testdisk) to try to recover the data.

---

### Post by Azgaroth on 2010-08-06
Silly me.
Thanks for the help mate. Shouldn't play around half asleep at first place. Buy buy data.

---

