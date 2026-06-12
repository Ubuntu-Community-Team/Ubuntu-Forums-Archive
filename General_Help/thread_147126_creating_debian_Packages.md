---
title: "creating debian Packages"
date: 2006-03-19
forum: General Help
---

### Post by Hairy_Palms on 2006-03-19
i have seen themes Packaged into .deb files for easy installation, i was wondering how you create them? all i ever read about is creating them from source code, but without source code how do u create them?
thanks in advance

---

### Post by tuxcantfly on 2006-03-19
use checkinstall

---

### Post by Hairy_Palms on 2006-03-19
no i mean i DOnT have ay source code, therefore i cant use checkinstall if you can use checkinstall to package things that AREnT source code plz tell me how

---

### Post by tuxcantfly on 2006-03-19
well, you could always open a deb package in ark, extract control.tar.gz and data.tar.gz, modify control in control.tar.gz to give it the name, description, and dependency information you need, and add your data files to data.tar.gz, save, then drag both new data.tar.gz and control.tar.gz back into the old deb, save the deb, then use dpkg -i on the new deb

---

### Post by psychicdragon on 2006-03-19
Another option is to use **apt-get source ** to get the source of one of the artwork packages, or any other non binary package. That way you can take a look at the rules and control files used by the packager.

---

### Post by Hairy_Palms on 2006-03-19
that doest work, iside cotrol ad data theres a directory just called . that gives a error if you try to add ay files too it

---

### Post by tuxcantfly on 2006-03-19
actually, don't add to the . directory. extract the files, modify them, and create a new archive called control.tar.gz.

same with data.tar.gz

then add the two archives to the original deb

---

### Post by Hairy_Palms on 2006-03-19
thanks :) that worked great :D i wasnt expecting it to be so easy

---

