---
title: "How to install Kile without installing half KDE?"
date: 2009-11-18
forum: General Help
---

### Post by iwan groznyj on 2009-11-18
Hello!

I'm running Ubuntu 9.10 (with Gnome) and want to install the LaTeX editor Kile which is a KDE programme.

So when I install the package "kile", Konqueror, Konsole and some other KDE applications are also installed because of the KDE dependencies.

Kile is the only KDE application I want to install on my system, and I want to keep my Gnome as clean as possible. (I just don't need two pdf viewers or two browsers… ;) )

How can I install the package only with the libs that are *really* neccessary to run Kile?

---

### Post by canadiandude007 on 2009-11-18
To find out the dependencies open Synaptic Manager, find the program then click on Properties.  You should see the list of all libraries that are required to make the program run, without all the others listed.

Or from the command line use:

sudo aptitude install <program name>

And it will alert you of all dependencies.

---

### Post by regala on 2009-11-18
> **iwan groznyj said:**
> Hello!

I'm running Ubuntu 9.10 (with Gnome) and want to install the LaTeX editor Kile which is a KDE programme.

So when I install the package "kile", Konqueror, Konsole and some other KDE applications are also installed because of the KDE dependencies.

Kile is the only KDE application I want to install on my system, and I want to keep my Gnome as clean as possible. (I just don't need two pdf viewers or two browsers&#8230; ;) )

How can I install the package only with the libs that are *really* neccessary to run Kile?

seems like it wants to install "Recommended" dependencies

edit (with sudo) /etc/apt/apt.conf, and add ```
Apt::Install-Recommends = 0;
```

or try running:
```
aptitude -R install kile
```

br,

---

### Post by iwan groznyj on 2009-11-18
> **regala said:**
> 
or try running:
```
aptitude -R install kile
```

That did it!

Many thanks! :D

---

