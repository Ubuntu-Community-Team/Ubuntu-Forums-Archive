---
title: "get .deb packages, no apt"
date: 2010-10-26
forum: General Help
---

### Post by Zeta-K on 2010-10-26
I have no internet at my house4, and the only place I have internet uses a Windows system. Is there any way to obtain packages from getdeb.net or playdeb.net from a windows computer to put on a flash drive and take home?

---

### Post by sisco311 on 2010-10-26
Here you go: [http://keryxproject.org/](http://keryxproject.org/) :)
and here:
[http://www.omgubuntu.co.uk/2010/09/keryx-offline-package-installation-made-easy-in-ubuntu/](http://www.omgubuntu.co.uk/2010/09/keryx-offline-package-installation-made-easy-in-ubuntu/)

---

### Post by katykat on 2010-10-26
Download from Windows.
Copy to a flash drive.
Copy to Ubuntu, in /tmp or any other convenient place.

Right click on them in nautilus - you should get the option to install them with Gdebi.

Else download Gdebi from a Debian archive (universe?) and install it with dpkg -i gdebi or whatever the full package name is.

Gdebi is alot better than dpkg and *should* integrate with the system.

---

### Post by katykat on 2010-10-26
Keryx appears to be for the main distros. 

The OP wants alternate sites.

---

### Post by EXCiD3 on 2010-10-27
Keryx works for any deb repository. If playdeb or other sites provide a repository you can add to your sources then it's all fair game! :-)

---

