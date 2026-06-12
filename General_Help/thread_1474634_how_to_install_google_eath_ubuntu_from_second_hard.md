---
title: "how to install google eath ubuntu? from second hard drive"
date: 2010-05-06
forum: General Help
---

### Post by gabak on 2010-05-06
hi
i never had a problem installing google earth but this time in this computer
i have two hdd.
i have download the google earth.bin in my second hdd.
i did chmod +x google earth.bin
then       sudo ./google earth.

and i got an error saying access denied.

but when i copied the file to my first hdd and i had no problem i could install it from there.
why is that?

---

### Post by ankspo71 on 2010-05-06
Try to open it with the "sh" command.

sh ./GoogleEarthLinux.bin  
(Installs to the home directory)

sudo sh ./GoogleEarthLinux.bin  
(Installs to the system directory)

I can confirm this works from my second hard drive with Kubuntu 10.04
> but when i copied the file to my first hdd and i had no problem i could install it from there.
why is that?
I think Ubuntu made it a little harder to run executables from outside sources, possibly for security reasons.

---

### Post by dcstar on 2010-05-07
> **gabak said:**
> hi
i never had a problem installing google earth but this time in this computer
i have two hdd.
i have download the google earth.bin in my second hdd.
i did chmod +x google earth.bin
then       sudo ./google earth.

and i got an error saying access denied.

but when i copied the file to my first hdd and i had no problem i could install it from there.
why is that?

Possibly because your second hard drive is not a Linux filesystem, but something crappy like FAT.

---

