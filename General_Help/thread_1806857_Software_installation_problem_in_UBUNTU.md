---
title: "Software installation problem in UBUNTU"
date: 2011-07-18
forum: General Help
---

### Post by ishabioinfo on 2011-07-18
Hello everyone,

I want to uninstall Python 2.6.5.
but when i am giving this command (as fallows) --

[COLOR=Blue]$ sudo apt-get remove python 2.6.5 [/COLOR] 

it is showing a error message -


[COLOR=Blue]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pyhton 2.6.5[/COLOR]

How to do uninstallation .
I have tried removal of thois software through synaoptic manager too but it was not working.

Thanks
isha

---

### Post by dino99 on 2011-07-18
sudo synaptic

and select the package(s) you want to remove, but you might check its dependants (right click on dependencies, then select the scroll menu "dependants")

note: you might talk about python2.6, its the latest default installation, so take care before removing it.

---

### Post by Wayne_V on 2011-07-18
the package is python2.6

get the version number from 'dpkg --list | grep python' or 'apt-cache showpkg python2.6'

then, you can remove with:

apt-get remove python2.6=2.6.5-1ubuntu6

although you will probably run into problems -- there are a lot of dependencies for python.

---

### Post by oldfred on 2011-07-18
DO NOT uninstall the default python install. There is no reason to uninstall it. You can install other versions if you like.

It is not just a lot of dependencies but most the system. It used to be you could not even chroot back into it to repair it as you had no Internet, but now I think you can at least do that. But in most cases it is easier just to start all over and reinstall.

---

### Post by Paventhan on 2011-07-18
try [sudo aptitude] instead of [sudo apt-get]

---

