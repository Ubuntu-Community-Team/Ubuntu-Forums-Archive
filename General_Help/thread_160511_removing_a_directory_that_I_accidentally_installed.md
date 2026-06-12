---
title: "removing a directory that I accidentally installed while installing an ATI-driver"
date: 2006-04-15
forum: General Help
---

### Post by elyna on 2006-04-15
Hie everyone.
I'm a newbie at linux and ubuntu.. so I know this might sound really stupid

I was following the instructions for installing ATI drivers [here ]("http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide") (Method 2) when I accidentally entered

LANG=C LC_ALL=C ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/breez

in the terminal instead of

LANG=C LC_ALL=C ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/breezy

yeah.. i missed out the 'y' in breezy :P
So anyways I reentered the correct comand and then the installation went fine. Right now I just wanna **remove whatever I did** when I ran the first command.
I hope my question is clear :\

My second question is.. I kinda install EasyUbuntu half-way through (err.... god knows why.. I just thought easy ubuntu will help me with installing the ATI drivers). Now I just wanna **remove** it.
I entered the following commands before giving up on it:

sudo apt-get install subversion
cd ; svn checkout svn://freecontrib.org/easyubuntu



Thanx a lot!

---

