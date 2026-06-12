---
title: "a gedit window appears on startup"
date: 2010-12-13
forum: General Help
---

### Post by doron387 on 2010-12-13
ubuntu 10.10/wubi/asus 1201n 
i have installed screenlets via synaptics and added two screenlets to my desktop.
i added screenlets to the autostart menu, pointing it to a folder inside my documents folder, where the launching icon of this software is located.
since then, after reboot a gedit window appears on my desktop and says the following :

[COLOR="Blue"]#!/usr/bin/env xdg-open

[Desktop Entry]
Type=Application
Categories=Utility;
Name=Screenlets
Name[de]=Screenlets
Name[et]=Screenlets
Comment=A graphical tool to manage your Screenlets.
Comment[de]=Ein grafisches Werkzeug, um Ihre Screenlets zu verwalten.
Comment[et]=Graafiline tööriist Screenlets vidinate haldamiseks
Icon=/usr/share/icons/screenlets.svg
Exec=screenlets-manager > /dev/null
StartupNotify=true[/COLOR]

how can i get rid of this window ?

doron387

---

### Post by sefs on 2010-12-13
1) Go to the directory in question and look for the icon.

2) Right click on it and in the menu select properties.

3) In the dialog box that pops up click on the permissions tab

4) look down until you see the execute label.  Across from label is a checkbox.  Ensure that it is checked to allow ubuntu to treat the file as executable.

That may fix it.

---

### Post by doron387 on 2010-12-13
it is checked as executable.
so it is probably not the solution.
any other strategies ?

---

### Post by sefs on 2010-12-13
> **doron387 said:**
> 
Exec=screenlets-manager > /dev/null


I can't think of anything else...but is the above line correct?

What you can do is try double clicking on the item and see what happens.

And in your terminal run
screenlets-manager to see what happens...

and then 
screenlets-manager > /dev/null

and see what happens.

---

### Post by sefs on 2010-12-13
> **sefs said:**
> I can't think of anything else...but is the above line correct?

What you can do is try double clicking on the item and see what happens.

And in your terminal run
screenlets-manager to see what happens...

and then 
screenlets-manager > /dev/null

and see what happens.

EDIT:
from this bug report here ... [https://bugzilla.redhat.com/show_bug.cgi?id=484644](https://bugzilla.redhat.com/show_bug.cgi?id=484644)

You can try opening the icon file in gedit and placing quotation marks around screenlets-manager > /dev/null so that it reads 
"screenlets-manager > /dev/null"

If that still does not work ... remove the "> /dev/null" part of the exec statement altogether and try that.

---

### Post by doron387 on 2010-12-14
> **sefs said:**
> EDIT:
from this bug report here ... [https://bugzilla.redhat.com/show_bug.cgi?id=484644](https://bugzilla.redhat.com/show_bug.cgi?id=484644)

You can try opening the icon file in gedit and placing quotation marks around screenlets-manager > /dev/null so that it reads 
"screenlets-manager > /dev/null"

If that still does not work ... remove the "> /dev/null" part of the exec statement altogether and try that.

[SOLVED], thanks, it worked.
doron387

---

