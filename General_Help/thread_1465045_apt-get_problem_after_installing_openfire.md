---
title: "apt-get problem after installing openfire"
date: 2010-04-29
forum: General Help
---

### Post by brian_centralpark on 2010-04-29
Hi,

I installed the Openfire Jabber server on an Amazon EC2 cloud instance of Ubuntu 9.10.  It seems that Ubuntu is no longer using the sun-java packages anymore and have gone to using openJDK.  

I installed the openJDK and jre packages.

When I went to install the openfire .deb package it said there were dependencies on sun-java packages that were not met and are not installable so it failed.  I overrode the dependency and forced the installation and changed the location of JAVA_HOME in the openfire start scripts and it works just fine.

However, I am no longer able to run apt-get install to install any other packages I need.  It fails due to unmet dependencies.  If I try to run apt-get -f install, it wants to remove openfire.
 
Is there anyway that I can have the package manager permanently ignore this problem with openfire (which is not a problem just a stale dependency) so I can go about my life happily installing packages?

Thanks,
Brian

---

### Post by valivarona on 2011-02-04
I got the same problem... my openfire works perfectly .. so I don't want to remove it. 
I guess that it should be a kind of hack ...
please HELP...
Valiku

---

### Post by valivarona on 2011-02-04
i got the solution
you have to change repositories.. to install sun-java6-jre


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner


after that .. sudo spt-get update
sudo apt-get -f install will install sun java

and it works

---

