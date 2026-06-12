---
title: "how to compile an offline installer of all codecs"
date: 2011-04-13
forum: General Help
---

### Post by elliotn on 2011-04-13
I currently have all restricted extras installed from java, gstreamer, etc and now want to compile them into a single tar.gz and make a one double click installer.  I have 4 friends to install to their pc with no internet. I found some simillar offline installers on the net but would like to make mine.

how do I do that

---

### Post by earthpigg on 2011-04-13
hi,

look in /var/cache/apt/archives

unless you have ran sudo apt-get clean, you will see a zillion .deb files in there - everything you've ever sudo apt-get isntall'd or installed from the software center or synaptic.

pick the packages you want, copy them to your desktop or wherever, and make your tarball. :)

if you want your buddies to have access to everything you've installed, grab every .deb you see.

next, you will want to make a simple shell script that extracts the tarball and installs every package it contains. hint: check out "man dpkg".

or, you can have the shell script copy these files to /var/cache/apt/archives on the local machine -- once this is done, the user will be able to sudo apt-get install gstreamer (etc) *without* an internet connection.

let us know if you need more detailed help than that - you sound like you are advanced/resourceful enough that you don't and only needed to be pointed in the right direction, but i could be wrong. :D

if you want to take a more advanced route, you can use your internet connection to download the ***entire*** ubuntu software repository onto an external hard drive that you can bring with you when you visit your friends. i think it's only like 40gb or something - not too crazy.

---

### Post by NFblaze on 2011-04-13
In addition to this, you will want to find out what each programs dependencies are (should be findable using apt-get or aptitude) and put those in the tar.gz

Then, to create an installer, you'd want to make sure that the user extracts them to a folder like RestrictedDebs then include an executable bash script that runs "gksudo dpkg -i ~/RestrictedDebs/*.deb" 

That command should then install the debs in the correct order and with the dependencies.

This is how Openoffice.org released their Debian install for there last RC candidate.

---

### Post by earthpigg on 2011-04-13
yup, the depends are why you may want to just grab every single package you've installed since installing ubuntu. much less labor intensive than venturing through [dependency hell]("http://en.wikipedia.org/wiki/Dependency_hell"), if you've got the hard drive space to do it.

---

