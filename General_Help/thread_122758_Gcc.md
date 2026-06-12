---
title: "Gcc??"
date: 2006-01-28
forum: General Help
---

### Post by TecSoft on 2006-01-28
I download GCC and I want to install it. How do I do it. I did ./configure and the last thing it said This release can't be compiled from source. I really need GCC for ndiswrapper. Anyhelp is apperciated.

---

### Post by dragos_avramescu on 2006-01-28
Could you just try 'sudo apt-get install build-essential' ? this installs gcc, too.
[http://www.ubuntuguide.org/#build-essential](http://www.ubuntuguide.org/#build-essential)

---

### Post by TecSoft on 2006-01-28
But I don't have internet connection. That is why I need to install ndiswrapper so I can get wifi internet.

---

### Post by hajk on 2006-01-28
There is already an ndiswrapper module in the Breezy kernel. All you need to use 
it to install ndiswrapper-utils package. 

Only if these don't work should you download the latest ndiswrapper source from SourceForge and compile it (it gives you both the module package and the utils package). You need to use gcc-3.4 for the compilation (not the newer gcc-4.0) because the kernel is also compiled with it. After installing 
the gcc-3.4 package with Synaptic, you should make sure that /usr/bin/gcc
is a symlink to /usr/bin/gcc-3.4

sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-3.4 /usr/bin/gcc

There is an entry on the Ubuntu-Wiki (SetupNdiswrapperHowto) that shows
how to do the compilation, including the small change to make to the debian/rules file to make sure the module is installed in the right directory.

Have fun!

---

### Post by TecSoft on 2006-01-28
Yeah it now works.

---

