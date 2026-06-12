---
title: "Problem installing Boxee? Associated helper?"
date: 2010-04-22
forum: General Help
---

### Post by schwabdale on 2010-04-22
When I download the Boxee.deb file and Try to install it, I get this error

could not be opened, because the associated helper application does not exist. Change the association in your preferences.

Any Ideas?

---

### Post by Lepy on 2010-04-22
I assume you downloaded the file from boxee.tv and the appropriate distribution.

Sounds like GDebi is not associated with .deb files for some reason.

Either right click on the files -> properties -> open with -> select GDebi Package Installer
Now double click on the package and follow on-screen prompts...

Or, open a terminal and type "sudo dpkg -i /path/to/boxee.deb

---

### Post by schwabdale on 2010-04-22
You were right. I Just had to open with Gdebi.

Thanks

---

