---
title: "Update issue in ubuntu 9.04"
date: 2010-02-25
forum: General Help
---

### Post by samusishere on 2010-02-25
Hi i am haveing a update issue in ubuntu 9.04 when i try to update from sudo apt-get update and the update manager i get this error.


W: Failed to fetch [http://javadesktop.org/lg3d/debian/dists/stable/contrib/binary-i386/Packages](http://javadesktop.org/lg3d/debian/dists/stable/contrib/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://javadesktop.org/lg3d/debian/dists/testing/contrib/binary-i386/Packages](http://javadesktop.org/lg3d/debian/dists/testing/contrib/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://javadesktop.org/lg3d/debian/dists/unstable/contrib/binary-i386/Packages](http://javadesktop.org/lg3d/debian/dists/unstable/contrib/binary-i386/Packages)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


what do i do? i have no idea what can be done now. please hep me. and this is the first time that i have posted a new topic on this fourm. so please if im in the wrong place please tell me.

---

### Post by donato roque on 2010-02-25
Hi 
try this.  It's a manual update.  Open a terminal by pressing 

Alt+F2

Then type "gnome-terminal", you will get your terminal.

On the Terminal please type:

~$ sudo apt-get update && sudo apt-get upgrade

This will update your system.

---

### Post by samusishere on 2010-02-25
HI, i tried this and it outputs the same error as before. as this depedency that it is unable to grab out of date???


 please helppppp!

---

