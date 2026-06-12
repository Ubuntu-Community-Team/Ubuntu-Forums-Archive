---
title: "easyubuntu!"
date: 2006-03-11
forum: General Help
---

### Post by styven on 2006-03-11
Hi all,

I tried out easybuntu and it seemed to be great, does what it says etc.

However upon doing a new install on another hard disk, and running easyubuntu again, things don't seem right.

For instance i checked for number lock to be activated upon boot, it don't.
Should be able to play dvd's, i can't.
The universe, multiverse repositries should all be added also.

And when i go to a shell to install something i get the following...........

styven@edubuntu:~$ sudo apt-get install libdvdread3
Password:
Reading package lists... Done
Building dependency tree... Done
libdvdread3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list cdrom://Edubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Edubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Edubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Edubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Edubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Edubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Edubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Edubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
styven@edubuntu:~$

This seems to be something to do with my cdrom?

Any ideas?

Steve

---

### Post by jasay on 2006-03-11
It's looking for the install cd to see if there are any packages you might want to install from it.  To get rid of the errors either put your cd in every time :p  or ```
sudo gedit /etc/apt/sources.list
``` and put a # in front of the line that says something about the cdrom (usually right at the top).  This will make the computer ignore that line and it will only look for packages online.  When you're done save and close the file and run ```
sudo apt-get update
```before installing anything.

P.S. you might have to [enable the universe or multiverse]("http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse") repositories to find certain packages.

---

