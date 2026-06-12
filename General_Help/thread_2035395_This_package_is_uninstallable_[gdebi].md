---
title: "This package is uninstallable?? [gdebi]"
date: 2012-07-30
forum: General Help
---

### Post by Mecasickle on 2012-07-30
Hi I'm trying to install an opensource package and I get this result on the terminal: 
  $ gdebi Gonzales_epfl_viva_diadem_x86_64.deb
  Building dependency tree   
  Reading state information... Done
  Building data structures... Done 
  Building data structures... Done 
  **This package is uninstallable
  Dependency is not satisfiable: libhighgui2.1 (>= 1.0)**


  The funny thing is that I have libhighgui2.1, because of OpenCV 2.3.1  I have installed. Or is this asking me for a version less than 1.0 of  libhighgui?


In stackoverflow, someone else answered the question with this:


**It's saying it doesn't *know* you have  "libhighgui2.1" installed.  There are several possible reasons.  Options  include: 1) force install (ignore dependencies) or 2) reinstall the  package (or allow dpkg/gdebi to reinstall it)** - randomuser1324 

link: [http://stackoverflow.com/questions/11727270/this-package-is-uninstallable](http://stackoverflow.com/questions/11727270/this-package-is-uninstallable)

To which I do not know how to force install or install by gdebi or dpkg. Reinstalling through synaptic hasn't been useful, so I'm not sure what to do exactly without breaking my previous installation of OpenCV-2.3.1

---

### Post by Mecasickle on 2012-07-30
* bump

---

