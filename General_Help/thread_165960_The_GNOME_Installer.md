---
title: "The GNOME Installer"
date: 2006-04-25
forum: General Help
---

### Post by chris062689 on 2006-04-25
I have heard that this installer is not very reliable at installing and removing packages, that sometimes the libaries from the programs get "left behind".

Is this true?
How would you rate the current (program) installer that comes with Ubuntu?
(NOT to install the OS, to install the actual programs!)

---

### Post by aysiu on 2006-04-25
Use *aptitude* instead of *apt-get*.

Read more about *aptitude* [here](http://www.ubuntuforums.org/showthread.php?t=164082).

---

### Post by chris062689 on 2006-04-25
Yes but, my major MAJOR turnoff, is that it has no GUI.

Is it really a PROBLEM to use the installer manager (thing?)?
I havn't booted into Ubuntu in a while, so I can't remember the exact program name.

---

### Post by aysiu on 2006-04-25
[QUOTE=chris062689]Yes but, my major MAJOR turnoff, is that it has no GUI.[/quote] I guess you have to decide how major a turnoff it is until they implement *aptitude* capabilities into Synaptic Package Manager.

---

### Post by jobezone on 2006-04-25
It is very reliable, all the files of a package you tell apt-get to remove, are removed, except configuration files within the system. To remove a package including these configuration files, one "purges" the package (with apt-get, synaptic, or adept). Your home directory isn't touched, so those configuration files placed by the app when you first launch it, and then use it, aren't removed.

You could look at apt-get + deborphan, or use aptitude.

---

### Post by aysiu on 2006-04-25
Good suggestion.

Yeah, if you absolutely need to use Synaptic and hate stray libraries, install *deborphan*, which locates programs on which other packages do not depend.

---

### Post by jobezone on 2006-04-25
After you learn the keys, aptitude is easy to use. See my quick overview on using aptitude at [http://jobezone.wordpress.com/2006/03/17/aptitude-in-30-seconds/](http://jobezone.wordpress.com/2006/03/17/aptitude-in-30-seconds/).
Nevertheless, when using ubuntu, I wouldn't necessarily recomend using aptitude, as I have no experience with it and ubuntu. Instead, I use synaptic and deborphan (as a filter, inside synaptic) in ubuntu.

---

