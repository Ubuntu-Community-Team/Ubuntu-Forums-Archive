---
title: "mixxx install help"
date: 2012-01-05
forum: General Help
---

### Post by n.foster on 2012-01-05
hey all, need some help, I want to install Mixxx, but I get this message in the terminal


Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 mixxx : Depends: libqt4-script (>= 4:4.5.3) but it is not going to be installed
         Depends: libqt4-sql (>= 4:4.5.3) but it is not going to be installed
         Depends: libqt4-svg (>= 4:4.5.3) but it is not going to be installed
         Depends: libqt4-xmlpatterns (>= 4:4.5.3) but it is not going to be installed
         Depends: libqt4-sql-sqlite but it is not going to be installed
E: Broken packages


is some one able to assist me, as to be honest I still have a lot to learn about Unbuntu.
I'm using 10.10 by the way

---

### Post by imachavel on 2012-01-05
check this out:

[http://www.mixxx.org/wiki/doku.php/compiling_on_linux](http://www.mixxx.org/wiki/doku.php/compiling_on_linux)

sudo apt-get build-dep mixxx
[sudo] password for danel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list


I seem to have the same error. idk is the answer I can provide. Try reading that though ;)

---

### Post by n.foster on 2012-01-05
thanks for the reply, I followed the link, and tried to follow it, but am still a little lost !

---

