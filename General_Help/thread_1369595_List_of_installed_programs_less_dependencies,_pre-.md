---
title: "List of installed programs less dependencies, pre-installed packages"
date: 2010-01-01
forum: General Help
---

### Post by Umang on 2010-01-01
The title says it all. I either want to know how to get the list, or I need clues on how to make a program that can do that.

I know that Ubuntu keeps track of how each package was installed. If I installed package ABC which depends on libXYZ, and I later uninstalled ABC, XYZ is now shown as auto-removable (unless something else depends on it). Ubuntu knows that I didn't install it myself, it was installed as a dependency.

I want a list of packages that ***I*** have installed, not as dependencies, not as pre-installed packages. Just the ones that I installyed myself (e.g only ABC, not libXYZ)

Any ideas?

This will be really helpful for people who can to do clean installs.

---

### Post by OldGrantonian on 2010-01-01
The following link might help:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Reinstalling_applications_after_a_fresh_install](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Reinstalling_applications_after_a_fresh_install)
.

---

### Post by Umang on 2010-01-01
No this isn't what I wanted. It doesn't subtract the appropriate packages. Dependancies and pre-installed packages are still installed.

However, I still know it is possible. Synaptic is able to mark a package as auto-removable if it was installed as a dependancy. We can use this to find out which were installed as new applications and which were installed as dependencies.

I also want to use this to clear some space (occasionaly). With this list, I can remove all the unneccesary packages, then the auto-removable ones thus delete all the unused packages off the computer. Here too, dependencies would complicate the matter too much.

---

### Post by Umang on 2010-02-01
I'm going to have to bump this thread, but I can be a bit more specifc.

Are there commands (e.g dpkg-*, apt-*) that I can call to complete the following steps (I'm going code a script for this)

1. Get a list of installed package
2. For each, find out whether it was pre-installed, or installed after install.
3. For each, check whether it has been installed as a dependency or actually installed through apt-get or aptitude.

Maybe start with "apt-cache pkgnames" then query "apt-cache policy foobar". Or is there any other way to find whether a package is installed or not (more machine readable). I'd like to use as little regex as possible.

For step 2, will subtracting the dependencies of ubuntu-desktop be sufficient? (dependencies of dependencies will be removed with step 3 anyway.

Would it be sufficient to see if a program has an rdepends that is installed to? (If it does I will remove it from my list).

---

### Post by Umang on 2010-02-02
I've found that someone else has already done this. But, I'm still going to write a python script for this (may or may not use deborphan)

Does anyone have any ideas on how to solve the circular dependency problem? i.e How do I get a keep at least one of the packages that circularly depend on one another. I can check if the package depends on the rdep, in which the case I can retain the package, but that would work only for a pair of packages. What do I do for the following situation:
pkgA (dep pkgB) -> pkgB (dep pkgC) -> pkgC (dep pkgD) -> ... pkgX (dep pkgA)

So many might not be probable, but trying to go three or four levels deep might take too long.

Any ideas?

Thanks

---

