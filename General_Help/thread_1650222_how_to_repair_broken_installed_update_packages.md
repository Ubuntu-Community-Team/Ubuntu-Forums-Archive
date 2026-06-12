---
title: "how to repair broken installed update packages?"
date: 2010-12-21
forum: General Help
---

### Post by dokha on 2010-12-21
"the following problems were found on ur sytem: there are multiple versions of 'drakconf' in your system this package wont be cleanly updated unless u leave only one version."
not only darkconf several other files too has the same error.
how to uninstall duplicates?

i left the pclinuxos update (via synaptic pckage manager) and wen i came back i saw the pc had shut down, and the above and bottom toolbars has dissappeared. and the above error wen i start the package manager.
how can i make a cd repair install? if this is the solution..
please help.

edit: i uninstalled duplicates but still the gnome deskop toobars still not there??

---

### Post by Rubi1200 on 2010-12-22
Hi,
to be honest, I think you would be better asking this question on the PCLOS forums.

That said, since you are using the GNOME version you could try this which will restore the panels to their defaults:

Warning: this will delete ALL custom settings you had for the panels. If you are willing to proceed:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```Log out and back in to see the changes.

Hope this helps.

---

