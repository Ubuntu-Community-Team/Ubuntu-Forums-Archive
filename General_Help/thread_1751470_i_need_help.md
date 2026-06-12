---
title: "i need help"
date: 2011-05-06
forum: General Help
---

### Post by LinuxNo0b445 on 2011-05-06
i have recently changed to linux ubuntu and i need help such as how to use downloaded content which doesnt seem to unpack properly. these things include Java. and i would also like to know how to check the system version. Thanks

---

### Post by dFlyer on 2011-05-06
> **LinuxNo0b445 said:**
> i have recently changed to linux ubuntu and i need help such as how to use downloaded content which doesnt seem to unpack properly. these things include Java. and i would also like to know how to check the system version. Thanks

from the command line type lsb-release -a will tell you which version your using. As for install programs I recommend you use synaptic or ubuntu software center. That way the correct libs get installed with the software. If you want to download a program and install it from the command line, make sure it's a deb file and use sudo dpkg -i file.name to install the program.

---

### Post by Rasa1111 on 2011-05-06
Hi and welcome linuxno0b,

Don't bother installing "java" on its own.

Instead, Open Ubuntu software center, and install "Ubuntu-restricted-extras"
(you shouldnt have to install/download anything from the web)

That will install flash, java, music/video codecs, all at once. 

To check your system version, Open "System Monitor" in your "Administration" menu,
and when it opens, click the "System" tab.

If you need anything else, just ask.

---

