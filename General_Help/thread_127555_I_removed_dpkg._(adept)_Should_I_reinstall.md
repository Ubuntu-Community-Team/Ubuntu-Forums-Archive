---
title: "I removed dpkg. (adept) Should I reinstall?"
date: 2006-02-09
forum: General Help
---

### Post by Prospero2006 on 2006-02-09
(Don't try this at home!)
Here's what I did:
     Adept-
       (-Remove dpkg)
           -It removed a like 3 different packages.
        -Now, of course, dpkg won't install anything.  
        -I'd like to replace it, but I don't mind reinstalling the O/S.
        -Is it possible to reinstate dpkg?

                  -Thanks
                     Prospero

---

### Post by gingermark on 2006-02-09
You took out the Daddy as well.

"It is important to understand that the higher level package management tools such as aptitude or dselect rely on apt which, itself, relies on dpkg to manage the packages in the system."

(from [http://www.debian.org/doc/FAQ/ch-pkgtools.en.html](http://www.debian.org/doc/FAQ/ch-pkgtools.en.html))

My guess is that you'll have to compile dpkg again. You could then use it to install .deb files of apt and whatever else went running (aptitude?).

That's a guess. God knows where you'd get the correct source from. And I have no idea if it would work. Good luck!

EDIT: If you decide to go down this route, the source code can be found [here](http://packages.ubuntu.com/breezy/source/dpkg)

---

### Post by newuser111 on 2006-02-09
im sure theres a way to chroot from a livecd or something but let someone with more experience post a way to install dpkg without having dpkg

---

### Post by stangbang on 2006-02-09
download the dpkg deb package and all of its dependancy's from here [http://packages.ubuntu.com](http://packages.ubuntu.com) then... O wait nevermind your screwed.

---

### Post by az on 2006-02-09
No, just compile it from source.  If you do not have build essential installed, you may use a live cd and install to another target.  I forget how....

---

### Post by az on 2006-02-09
...from the dpkg manpage



       --root=dir | --admindir=dir | --instdir=dir
              Change   default   directories.    admindir  defaults  to
              /var/lib/dpkg and contains many files that give  informa&#8208;
              tion  about  status of installed or uninstalled packages,
              etc.  instdir defaults to / and refers to  the  directory
              where  packages are to be installed.  instdir is also the
              directory passed to chroot(2)  before  running  package’s
              installation  scripts,  which  means that the scripts see
              instdir as a root directory.  Changing root changes inst&#8208;
              dir to dir and admindir to dir/var/lib/dpkg.

So, you would boot the installer and mount your partition somewhere (say /mountpoint).  You would cd to the dpkg deb on the cd and run
dpkg -i dpkg*.deb --root =/mountpoint

..I think....

---

### Post by Prospero2006 on 2006-02-09
All of those are valid solutions. 
However, I wasn't in too deep with the install. 
It was easier to just drop a new install clean.
I thank you all for the help. (It was educational)
I'm sure if I had to make it work I could.


Thanks,
Prospero

---

