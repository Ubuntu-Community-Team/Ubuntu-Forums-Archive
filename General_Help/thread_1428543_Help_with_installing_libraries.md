---
title: "Help with installing libraries"
date: 2010-03-12
forum: General Help
---

### Post by GEFORCEXTREME on 2010-03-12
Hi, I'm a new Ubuntu user. There is one thing I'm confused about. Sometimes when I run the configure script (./configure) of some program distribution, it says I don't have library x and when I go to The Synaptic Manager, it says it is there.

Most of the time what these scripts mean is that I don't have the development (dev) version of these libraries.

Why is there a dev version and a non-dev version of some libraries?

And, how do I master the use of Synaptic Manager? Most of the time, some configure scripts say I don't have x and when I search for x, there are multiple x related items, how do I know which one do I really need? By experience? The description sometimes don't say much.

Sorry, if my questions seem stupid, but please guide me. Thanks.

---

### Post by Agent ME on 2010-03-12
The "something-dev" packages contain the information for you to compile something that uses the library. It's not needed for pre-compiled stuff, such as other programs also in the repository. A system that never has anything compiled on it does not need any of the "something-dev" packages.

If you're unsure of what package you need when it's reported that a certain library is missing, try googling the name of the library plus "ubuntu" or "package", etc.

---

### Post by nemilar on 2010-03-12
Hello... 

I'm curious if you might be going down the wrong path when you're installing applications.  It looks like you are trying to compile applications by hand on your machine; while there's nothing specifically *wrong* with that, and it is a good learning experience, it's definitely not the best way, and you should only do it if there is no pre-compiled package available.

Specifically, what application are you trying to install? 

Ubuntu has a built-in package management and repository system.  Most of the more common packages are available through it, and you should use this system because it allows the OS to track what is installed, what needs to be installed as dependencies, etc..  This is especially useful when it comes time to uninstall, because you can issue a single command and the system will figure out what can/needs to be removed.

Edit: from the command line, you might try issuing this command, to see if the package you want is available:
```
apt-cache search [package name]
```

Example:
```
apt-cache search firefox
```

---

