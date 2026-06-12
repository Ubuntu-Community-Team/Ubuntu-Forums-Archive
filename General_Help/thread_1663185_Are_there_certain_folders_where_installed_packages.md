---
title: "Are there certain folders where installed packages go?"
date: 2011-01-09
forum: General Help
---

### Post by Toxicbits on 2011-01-09
Hi,

I was just wondering how installed packages are structured. 
It seems quite complicated to me, when I browse my folders. 
Are there different folders for applications and settings? Are there different settings-folders for each user? 
Why is there an Opt folder and and a single folder for games under \usr?

I'm Ubuntu user for quite a while now but I still dont get it. Maybe it would be useful to make that a lot more transparent?

---

### Post by QLee on 2011-01-09
[QUOTE=Toxicbits]Hi,

I was just wondering how installed packages are structured. 
It seems quite complicated to me, when I browse my folders. 
Are there different folders for applications and settings? Are there different settings-folders for each user? 
Why is there an Opt folder and and a single folder for games under \usr?

I'm Ubuntu user for quite a while now but I still dont get it. Maybe it would be useful to make that a lot more transparent?[/QUOTE]

Either have a look at this site:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html)

...or, enter the command, man hier, in a terminal window to read the manual page.


[Edit] you might not find this under home but to answer your question, "Are there different settings-folders for each user?", yes those are the folders under /home for each username on a default multi-user install.

---

### Post by AlphaLexman on 2011-01-09
Most binary files or 'programs' are found in the directories in your $PATH variable; ```
cat $PATH
``` There are system binaries, user binaries, and local binaries. The linux filesystem puts these in different locations. You may have more than one version of a program and it would be stored in seperate locations.
> Why is there an Opt folder and and a single folder for games under \usr?
Games are found in /usr/games. The /opt directory is probably there for historical reasons. It gives an optional place to save files.

---

### Post by Toxicbits on 2011-01-09
Thanks for your answers. But is there any need to keep these orphaned folders like \opt?

---

### Post by QLee on 2011-01-09
No, there is no real need to keep an empty folder that you are never going to use on your filesystem, and I suppose you'll never use it as long as no software installs there, now or in the future. They don't take much space though.

---

### Post by oldos2er on 2011-01-09
```
dpkg -L <package>
``` shows you where each file in a package is installed. You can see the same thing in Synaptic; right-click on an installed package, Properties, Installed Files.

To understand Linux file system hierarchy, see [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by perspectoff on 2011-01-09
+1

Yeah, the package system in Debian / Ubuntu /Kubuntu has a certain expectation of certain folders. Sure, you can erase anything you want, but then you negate the benefit of having a somewhat standardized distro like Debian / Ubuntu / Kubuntu. 

For the specific question of where (i.e. into which folders) the individual files of a package are installed, you can see this from Synaptic Package Manager (or KPackageKit in Kubuntu).

Find the package you are interested in, click on the name of the package for details, and the folders into which the components have been installed will be displayed.

This is by far the easiest way.

---

