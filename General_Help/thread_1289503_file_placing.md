---
title: "file placing"
date: 2009-10-12
forum: General Help
---

### Post by PowerSource on 2009-10-12
I'm almost completely migrating to ubuntu from windows, though there is one big thing that I haven't understood yet.


in windows there is one big folder called "programs". when you are installing a program it often asks where it shall place itself and then you just pick the program folder. if you want to remove a program it is often enough with just removing that folder.

in linux though, it seems like when you use a .deb file or use "install/remove programs" and you search for the programs name, the results end up in about 5 folders in completely different places.
one is for the copyright and one is for the bin files and one is for the pics and so on.

why have linux chosen this (for me) weird way of placing files that makes it really hard to completely remove a program using nautilus?

---

### Post by mcduck on 2009-10-12
Because storing each file together with other files that have similar purpose actually makes a lot of sense (for example keeping documentation for all your programs in /usr/share/doc and executable files for all your programs in /usr/bin).

And because you are never supposed to remove programs manually, that's what the package manager is for.

Believe me, it will start to make a lot of sense when you learn the locations where different types of files are kept.

edit: besides, removing the program's directory in Windows rarely removes the program completely. In most cases you still end with lots of unnecessary stuff in your registry, and quite often programs actually even put some files in the system directories. At least Linux has a working system to properly handle this kind of things and doesn't need a huge registry file to track all the file locations for the programs.. ;)

---

### Post by PowerSource on 2009-10-13
> **mcduck said:**
> 
And because you are never supposed to remove programs manually, that's what the package manager is for.


well, if you install the program using a .deb file, what are you then supposed to do?

---

### Post by diesch on 2009-10-13
See the [hier manpage](http://manpages.ubuntu.com/manpages/jaunty/en/man7/hier.7.html) for a quick overview of the file system hierarchy and [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/) for the full story.

---

### Post by uberg on 2009-10-13
When you are installing a .deb file from nautilus the Package Manager installs the program.  Once it's installed and you later want to remove use Synaptic to uninstall the program.  It takes care of nearly everything.

---

### Post by mcduck on 2009-10-13
> **PowerSource said:**
> well, if you install the program using a .deb file, what are you then supposed to do?

Uninstall it with the package manager.

All programs installed from .deb packages are registered by apt, and can be removed using dpkg, apt-get, Synaptic or any other package management tool. In the end all these tools are just more complicated front ends to the very same dpkg that is used to install .deb packages you have downloaded yourself. 

(note that the Add/Remove is not a full-blown package management tool so it will not show manually installed packages, just like it doesn't even show all packages available in the repositories)

Even programs installed manually from source code can be uninstalled with the package management if you use checkinstall to install them. The only situations when you'd have to uninstall program manually is if you installed something by compiling from source code (without using checkinstall) and the program didn't come with uninstall script, or if you installed something using a binary installer (and once again it didn't come with uninstaller).

---

