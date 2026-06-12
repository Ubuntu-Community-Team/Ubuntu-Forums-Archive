---
title: "Opening Adept"
date: 2006-04-26
forum: General Help
---

### Post by SolidSnake2 on 2006-04-26
When I open Adept from the K MEnu, it says It can only be in read only mode, and to install programs I must open it in the root. How can I do that.

---

### Post by Harold P on 2006-04-26
Open up Konsole, and type:
sudo adept

I think will work?

---

### Post by DoeRayMe on 2006-04-26
^^^ should never use sudo to launch KDE apps

use:

> kdesu adept

---

### Post by Harold P on 2006-04-26
Oh, I see. I'm new to KDE. :oops:

---

### Post by SolidSnake2 on 2006-04-26
When I typed in kdesu adept, it still launches in "read only mode" still, anyone know at all what now?

---

### Post by gingermark on 2006-04-27
You could try right clicking on the menu entry and selecting "Edit Item". The menu editor will open. For the Adept entry try selecting "Run as different user" (Username: root), saving the changes, and trying again.

I fear this will be just as effective as kdesu was, but might be worth giving it a go.


And yes, ONLY use sudo for commands (like apt-get).
To lauch graphical apps with root priviledges, use 'kdesu' in Kubuntu and 'gksudo' in Ubuntu.

---

