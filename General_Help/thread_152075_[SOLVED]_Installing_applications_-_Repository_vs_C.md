---
title: "[SOLVED] Installing applications - Repository vs CD Drive"
date: 2006-03-29
forum: General Help
---

### Post by Goldpin on 2006-03-29
I'm waiting for my Breezy CDs to arrive, but I have a question about installing applications.

Obviously you can install from the repository using apt get.  However, as I only have dial up internet access this could take an inordinate amount of time.  :(

I do have access to broadband, but not at home.  Is there any way of downloading the packages I want, burning them onto CD and then installing them at home?  The programs could come either from the repository or directly from a site (getting OpenOffice 2.0.2 from the OpenOffice site for example).

Since I'm a complete newbie, any suggestions would be greatly appreciated.

---

### Post by alamba on 2006-03-29
Absolutely buddy. Just download the .deb files of the application you need and use dpkg -i <package_name.deb> to install.

A

---

### Post by aysiu on 2006-03-29
Check out [the Add-on CD project](http://www.ubuntuforums.org/showthread.php?t=136955).

---

### Post by StefanoCole on 2006-03-30
Also, if you have to install more packages and manage dependencies you could build a local repository. To this purpose this link helps:
[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html")

Stefano

---

