---
title: "libqt4 (ktoon, pencil) fails to install in ubuntu 10.10 64bit"
date: 2011-04-07
forum: General Help
---

### Post by cdrKeene on 2011-04-07
I'm trying to install either ktoon or pencil. I've tried .deb packages outside of the repos, and either way Qt4 is a requirement. Attempts to install libqt4-core give the following errors in synaptic:

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.7.0-0ubuntu4.2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.7.0-0ubuntu4.2_amd64.deb)
  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.7.0-0ubuntu4.2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.7.0-0ubuntu4.2_amd64.deb)
  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-test_4.7.0-0ubuntu4.2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-test_4.7.0-0ubuntu4.2_amd64.deb)
  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/q/qt4-x11/libqt4-core_4.7.0-0ubuntu4.2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/q/qt4-x11/libqt4-core_4.7.0-0ubuntu4.2_amd64.deb)
  404  Not Found


I navigated to the url listed in the error manually to see if the name had changed slightly or if there was another option. I downloaded what I thought was the appropriate core package to see if i could add all of the dependencies package by package. The above error lists:>  libqt4-core_4.7.0-0ubuntu4.2_amd64.deb. The Folder contains: > [libqt4-core_4.7.0-0ubuntu4.3_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/universe/q/qt4-x11/libqt4-core_4.7.0-0ubuntu4.3_amd64.deb")I'm just guessing left and right. Installing any of the packages before installing libqt4-core lists libqt4-core as a dependency. attempting to install [libqt4-core_4.7.0-0ubuntu4.3_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/universe/q/qt4-x11/libqt4-core_4.7.0-0ubuntu4.3_amd64.deb") (the difference is the .3 instead of .2) gives the following dependency error in the Ubuntu Software Center: 
> Dependency is not satisfiable: libqtcore4 (= 4:4.7.0-0ubuntu4.3) so now I'm just really lost. Something tells me the solution is simple and/or it's just not a supported package anymore? (something like that happened to me before) I'm a newb and I just have no idea ^_^!

any help would be greatly appreciated

---

### Post by cdrKeene on 2011-04-08
Solution: magic. 

It works now. I guess something got updated. Thanks, somebody!

---

