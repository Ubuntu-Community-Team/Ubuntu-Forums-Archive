---
title: "install package"
date: 2012-02-18
forum: General Help
---

### Post by Nirav32 on 2012-02-18
I want to install some package
It has following dependence.
gdk-imlib11
imlib11
libc6...etc
how I can install gdk-imlib11 and imlib11 packages.

I try to manually download and install using dpkg -R -i *.deb
it require other sub dependence.
Then I restart but again it didn't start.
I have to again format and install fresh Ubuntu.

I search imlib11 in Synaptic package manager but nothing found.
I try apt-get install imlib11_1.9.15-6_i386.deb , but it can not find.

What is correct way to install package gdk-imlib11 and imlib11 package so it automatically download and install sub dependence.

Please Help...

---

### Post by cogier on 2012-02-18
This seems strange as the "dependencies" you require don't seem to exist.

The Terminal command **aptitude search imlib11** comes up with nothing. This means that there is no such dependency available from the normal repositories.

I suggest you advise us what "..some package.." is so that we can help you further.

---

### Post by forrestcupp on 2012-02-18
This is a great example of why it's not a good idea to install any random deb that you found to download. Maybe you should check with the devs of the program you're trying to install to see if they have a PPA that works with Ubuntu or if they have their own resources with all of the dependencies they require.

---

### Post by Nirav32 on 2012-02-18
I try to install [http://packages.ubuntu.com/hardy/cheops-ng](http://packages.ubuntu.com/hardy/cheops-ng)
It is network management application.
  	 	 	 	 	 	   I has many dependencies
 I download all that but not sub dependencies.

---

### Post by Leppie on 2012-02-18
gdk-imlib11 is only in the Hardy repo. This must be a very old application you're trying to install. [http://packages.ubuntu.com/hardy/gdk-imlib11](http://packages.ubuntu.com/hardy/gdk-imlib11)

---

### Post by forrestcupp on 2012-02-18
If you're not using Hardy, it would be a big mistake to try to install that. You're going to end up downgrading a bunch of dependencies to very old versions, and it's going to be a huge mess and probably screw up a lot of other things. They've worked really hard to get rid of dependency hell, but this is an example of how you can force it to happen.

You seriously need to find an alternative program that will work better with more modern releases of Ubuntu. Trust me; you'll end up being sorry if you try to force this through.

---

