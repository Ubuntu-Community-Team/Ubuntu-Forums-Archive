---
title: "problems removing wine programs"
date: 2011-02-11
forum: General Help
---

### Post by kooley on 2011-02-11
hello, im having a little problem removing wine programs.

firstly i tried going into the wine menu and selecting uninstall under the programs tab in the menu, it said it was successfully uninstalled but if failed to remove anything.

then i tried "uninstall wine software" under the wine tab and that still didn't change anything.

finally i tried removing wine itself with "sudo apt-get remove wine"
again it said wine was successfully removed, and again nothing changed wine and all its programs are still here.

how can i get rid of it?

---

### Post by DanneStrat on 2011-02-12
To get rid of all your wine programs

do the following:

Carefully copy and paste the following commands

in a terminal one by one (press enter after each one)

```

rm -rf $HOME/.wine

rm -f $HOME/.config/menus/applications-merged/wine*

rm -rf $HOME/.local/share/applications/wine

rm -f $HOME/.local/share/desktop-directories/wine*

rm -f $HOME/.local/share/icons/????_*.{xpm,png}

rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png}


```

That should remove the hidden .wine folder

containing all the applications and also

clear out the system menus of any

residues like shortcuts etc.

---

### Post by kooley on 2011-02-12
ok thank you :) 

now my problem is when i reinstalled wine after finally removing all the programs wine no longer appears under my "K menu"

---

### Post by DanneStrat on 2011-02-13
> **kooley said:**
> ok thank you :) 

now my problem is when i reinstalled wine after finally removing all the programs wine no longer appears under my "K menu"

It seems like wine didn't update the kmenu

and it can happen sometimes.

Install the "kmenuedit" package and you can

add wine to the menu manually.

Some info on how to do it:

[http://docs.kde.org/stable/en/kdebase-workspace/kmenuedit/quickstart.html](http://docs.kde.org/stable/en/kdebase-workspace/kmenuedit/quickstart.html)

---

### Post by kooley on 2011-02-13
ok thank you guys for helping it worked perfectly :)

---

