---
title: "Difference between installing from a .deb file and package manger?"
date: 2010-05-17
forum: General Help
---

### Post by mahela007 on 2010-05-17
I installed mozilla thunderbird a few months ago (why isn't that the default mail client in Ubuntu? ) using a .deb file. However, with this method, I had to find an icon for the start menu entry manually and there is no way for selecting Thunderbird as the preferred application in the preffered applications menu. Also, I can't configure the desktop applet to open thunderbird instead of evolution when I want to send mail. There is a drop down list for selecting a different mail client but thunderbird is not listed. 

Since I noticed all these little discrepancies, I'm wondering what the difference is between installing form a .deb file and the repos.
thanks

---

### Post by R3VAMP3D on 2010-05-17
Knowing Linux package management internals, there really is no difference other than one is a manually retrieved package. If the package in question didn't have the proper artwork (licensing issues?) then thats why. Packages you pull from repositories are just read from an index, the database, (what happens when you apt-get update), and then apt-get install reads this database and pulls the package listed in memory. There should be no difference besides whoever built it may have built it different and/or wrong

---

### Post by 3rdalbum on 2010-05-17
There should be no difference (the repositories contain Debian packages [.deb files]) but sometimes a package is built differently by a different person; obviously they haven't included the special sauce that allows it to be an option in the Preferred Applications settings, although you can put it as "custom".

---

