---
title: "How To Upgrade a Library"
date: 2011-08-27
forum: General Help
---

### Post by mark bower on 2011-08-27
What is the syntax for upgrading a specific library.  Library "libdbus-glib-1-2 is already installed as ver 0.80; it must go to 0.82 or higher (0.88 is available) I entered the following:

sudo aptitude install libdbus-glib-1-2

Everything looks good as the lines read in, until the line "No pkgs will be installed, upgraded or removed".

mark bower

---

### Post by Frogs Hair on 2011-08-27
What version of Ubuntu ? The current version of that package for 11.04 is libdbus-glib-1-2 0.92
You may find what you need at the link.[http://pkgs.org/ubuntu-10.10/ubuntu-main-i386/libdbus-glib-1-2_0.88-2_i386.deb.html](http://pkgs.org/ubuntu-10.10/ubuntu-main-i386/libdbus-glib-1-2_0.88-2_i386.deb.html)

---

### Post by mark bower on 2011-08-28
i am using 10.10

i downloaded libdbus-glib-1-2_0.88-2_i386.deb (did not realize that libraries were updated via .debs) and now yet another library is requested.  did it, but then would not install because another library was requested.  so allow me to restate the problem.

to see a floppy 1.44 inserted before boot, on one of my computers, i simply entered the command "udisks -mount/dev/fd0" in a desktop launcher. it works like a charm.  and unmount when done.  there was no fussing with any libraries.

so i intended to repeat on another computer, 10.10 and same m/b, and i get messages which indicate dependencies and seems i have to get to the bottom of the heap (dependencies), then work my way back up installing one .deb after another - and i am getting in a little over my head.

it all started after installing "udisks_1.0.1-1build1_i386.deb"

so is there a way to install the udisks . . library above and have it pull in all of the libraries it is dependent upon?    

or, when  i go to Syn Pkg Mgr, set to  "ALL", and enter "udisks_1.0.1-1build1_i386.deb", a search does not show the file?  am i doing something wrong here?  it is my  understanding that Syn Pkg Mgr should pull in all the dependencies, am i correct? 

mark bower

---

### Post by raja.genupula on 2011-08-28
open synaptic manager 
in search box , type the library what you're looking . if its have upgrade then it gonna show you

---

### Post by thi3000 on 2011-08-29
first of all you should only DL the libraries that are supplied to you. As in when you install a package, just do as the installer says. I know sometimes it seems necessary to update and install certain things but really, Ubuntu will do it all for you. You don't really need to install any more libraries.

---

### Post by mark bower on 2011-08-29
thanks for replies, but maybe i am still not clear enough.

on one machine, i set up a floppy launcher which uses "udisks".  i did nothing else.  with synaptic, i can see that "udisks_1.0.1-1build1_i386.deb is installed.

so, when trying to establish the launcher on another machine, i received an error msg.  using synaptic, i saw that the udisks library was not present.  so i assumed i merely had to install it and then could create the launcher.  but as i attempted to install it, it indicated that another library was absent.  and this continues with a given library wanting some other library before the given library will install.

if i enter the udisks library in the search box in Syn Pkg Mgr, it does not discover the library.  what i thot would happen from previous experience is that after making the udisks entry in synaptic, that it would be discovered along with dependencies and then all would be installed; not the case.

and again, as far as i know, i installed 10.10 on both machines the  same way.

hopefully this better explains what i am trying to do and how to resolve the problem.

as a work around, i believe i can do the following which works at least on the machine where the launcher already conveniently does the job:

sudo mkdir /floppy
sudo mount /dev/fd0 /floppy -vfat

mark bower

---

### Post by mark bower on 2011-09-03
o.k.,  things did not work out for me on this post.  i will not return to it and consider it dead.

---

