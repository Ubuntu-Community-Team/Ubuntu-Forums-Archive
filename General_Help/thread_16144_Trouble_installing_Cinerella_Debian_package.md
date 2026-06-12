---
title: "Trouble installing Cinerella Debian package"
date: 2005-02-19
forum: General Help
---

### Post by GreyGhost on 2005-02-19
i add the repository that contains cinerella, I locate it in the Synaptic Package manager & mark it for installation. This is what i get back

[I]cinelerra:
  Depends: libasound2 but 1.0.5-woody0.1 is to be installed
 Depends: libavcodec1 but it is not going to be installed
 Depends: libguicast but it is not going to be installed
 Depends: libmpeg3hv but it is not going to be installed
 Depends: libopenexr2 but it is not installable
  Depends: libpng12-0 but 1.2.5.0-7 is to be installed
 Depends: libquicktimehv but it is not going to be installed[/I]

This is the relevant section of my sources.list
## THESE ARE FOR CINERELLA
deb [http://www.kiberpipa.org/~minmax/cinelerra/builds/pentium4/](http://www.kiberpipa.org/~minmax/cinelerra/builds/pentium4/) ./ 
deb-src [http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/](http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/) ./
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

i can find each one of the Depends in my Synaptic Package Manager, but most wont install due similar dependancies listed above.

If anyone could help that'd be great (or try to install cinerella yourselves, its suppose to be the best video editor for linux). Or if any one could lead me in the right direction that'd be great also.

Thanks in advance :-P 

GreyGhost

---

### Post by az on 2005-02-19
The binary package you want to install has incompatibilities with the packages you have installed.  That is why it refuses to install.

It was probably made for debian, and if you were running debian with packages only from debian you would not have this problem.

You can always get the source and compile it.  Since it already runs on debian, you can always add (if you do not already have) the deb-src entries into your repository listing and 
apt-get build-dep cinelerra
apt-get source cinelerra

and make the package for Warty.

---

### Post by ajuss on 2005-04-25
[QUOTE=azz]The binary package you want to install has incompatibilities with the packages you have installed.  That is why it refuses to install.

It was probably made for debian, and if you were running debian with packages only from debian you would not have this problem.

You can always get the source and compile it.  Since it already runs on debian, you can always add (if you do not already have) the deb-src entries into your repository listing and 
apt-get build-dep cinelerra
apt-get source cinelerra

and make the package for Warty.[/QUOTE]
 or you could download cinerella rpm package from the cinerella download area
**alien cinerella*.rpm** (good thing it has all dependencies included in rpm)
and you get yourself cinerella*.deb
then just
**sudo dpkg -i cinerella*.deb** 
then use menueditor to add to menu, u can find cinerella executable in usr/bin
worked for me

---

### Post by ajuss on 2005-04-28
[QUOTE=ajuss]or you could download cinerella rpm package from the cinerella download area
**alien cinerella*.rpm** (good thing it has all dependencies included in rpm)
and you get yourself cinerella*.deb
then just
**sudo dpkg -i cinerella*.deb** 
then use menueditor to add to menu, u can find cinerella executable in usr/bin
worked for me[/QUOTE]
 this site includes cinerella deb package
[http://cvs.cinelerra.org/index.html](http://cvs.cinelerra.org/index.html)
February 8, 2005
x86 Debian packages of Cinelerra 1.2.2 by Andraz Tori.
Use the [apt source](http://cvs.cinelerra.org/packages.html#apt-x86)  to get it.

---

### Post by bigkahuna on 2005-05-04
> or you could download cinerella rpm package from the cinerella download area
alien cinerella*.rpm (good thing it has all dependencies included in rpm)
and you get yourself cinerella*.deb
then just
sudo dpkg -i cinerella*.deb
then use menueditor to add to menu, u can find cinerella executable in usr/bin
worked for me

I tried this and got this:

> cinelerra: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory

Any idea where this?

Thanks

---

