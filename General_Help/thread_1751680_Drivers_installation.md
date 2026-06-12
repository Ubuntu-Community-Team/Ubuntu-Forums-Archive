---
title: "Drivers installation"
date: 2011-05-06
forum: General Help
---

### Post by Nerijus1 on 2011-05-06
Hey all!
After all night studying "Ubuntu" system, i finaly downloaded almost all programs i needed, and now i need to install my graphic drivers, but when i download them and lounch, i get an error, that they must be lounched as "root" user, can anyone help me to switch that user? if its possible? :oops:

---

### Post by cymbaline42 on 2011-05-07
Use sudo [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

sudo apt-get install [package name]

---

### Post by 3rdalbum on 2011-05-07
Read the link that was posted above, it's something that you'll need to know to understand Ubuntu's security system - in fact, you'll need to know the difference between user and administrator for ANY new operating system.

However, you shouldn't be installing your graphics driver manually. Go to System > Administration > Additional Drivers to download and install them, or if you're using Unity go to the on/off icon, then System Settings, then Additional Drivers.

---

