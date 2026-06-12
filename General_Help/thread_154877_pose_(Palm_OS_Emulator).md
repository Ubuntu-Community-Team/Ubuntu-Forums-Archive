---
title: "pose (Palm OS Emulator)"
date: 2006-04-04
forum: General Help
---

### Post by chrisbtoo on 2006-04-04
Hi all,

I'm trying to install pose (palmos emulator) but it's failing due to a dependency on libfltk1.

I can install libfltk1.1, but that seems to be insufficient.

Output from an attempt to install pose:

[FONT="Courier New"]
% sudo apt-get install pose
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pose: Depends: libfltk1 but it is not installable
E: Broken packages[/FONT]

And for libfltk1:
[FONT="Courier New"]
% sudo apt-get install libfltk1
Reading package lists... Done
Building dependency tree... Done
Package libfltk1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libfltk1 has no installation candidate

[/FONT]

Anyone had any success installing either of these packages, or should I raise a bug as apt suggests?


Chris.

---

### Post by Cephyr on 2006-04-04
I don't believe it's a bug. It simply means that while libfltk1 is NOT in the repositories, another package depends on it. I would try googling for libfltk1 and trying to a find a .deb package for it, and then using "sudo dpkg -i" to install it.

Hope that helps!

---

### Post by erickrdch on 2006-08-16
i have successfully installed pose in my Ubuntu dapper. What i did was to download Debian oficial package, then i tryed to install it directly but i has a dependency that exist in Ubuntu but it has a different name, so i fix the package to change dependenci name and it works perfectly, if you still need this file or instructions in how to fix the .deb package email me. [email]erickrdch@gmail.com[/email] ;)

ps. sorry for my bad english.

---

### Post by kostkon on 2006-08-16
Last year I installed the *pose* from the official debian deb in Ubuntu 5.04 and I didn't have any dependency problems (as I remember). I assume, now there is a new version for debian, that creates dependency problems in Ubuntu.

---

### Post by erickrdch on 2006-08-16
yeah, the problem with dapper deppendency is this:

debian: libfltk1.1c102
ubuntu: libfltk1.1

i already post how to fix that here: [http://www.ubuntuforums.org/showthread.php?p=1386481#post1386481](http://www.ubuntuforums.org/showthread.php?p=1386481#post1386481)

interesting to fix dependencies names, i learned that fixing a previous skype version

---

