---
title: "Firefox dead after security update"
date: 2010-01-08
forum: General Help
---

### Post by Exüberance on 2010-01-08
I just recently (like an hour ago) let Ubuntu do a security update. It updated firefox, GIMP, and xulrunner (which affects firefox). Firefox was working perfectly before the update, but when I did the update, xulrunner 1.9 failed to install, returning a non-zero exit status. Firefox was updated, however, to use xulrunner 1.9 (that part of the update worked), but xulrunner doesn't exist since it won't install. Attempting to start firefox gives a message about not being able to find GRE with version 1.9.* (since xulrunner failed to install)

Any way I can fall back to the last firefox update before this one until the problem is fixed?

---

### Post by Exüberance on 2010-01-09
bump

---

### Post by DeMus on 2010-01-09
> **Exüberance said:**
> bump

You could try to un-install Firefox and Xulrunner using Synaptic and afterwards install it again. That's about all you can do, I think.

---

### Post by Exüberance on 2010-01-09
I tried that, but xulrunner will not install no matter what I do. Here's the errors I'm getting:

sudo apt-get install xulrunner
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xulrunner-1.9.1
Suggested packages:
  xulrunner-gnome-support
The following NEW packages will be installed:
  xulrunner
The following packages will be upgraded:
  xulrunner-1.9.1
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
60 not fully installed or removed.
Need to get 0B/9,400kB of archives.
After this operation, 1,077kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 239038 files and directories currently installed.)
Preparing to replace xulrunner-1.9.1 1.9.1.6+nobinonly-0ubuntu0.9.10.1 (using .../xulrunner-1.9.1_1.9.1.7+nobinonly-0ubuntu0.9.10.1_amd64.deb) ...
Unpacking replacement xulrunner-1.9.1 ...
/rm/rm: cannot remove `/usr/lib/xulrunner-1.9.1.6/python/xpcom/__init__.pyo': No such file or directory
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/rm/rm: cannot remove `/usr/lib/xulrunner-1.9.1.7/python/xpcom/__init__.pyo': No such file or directory
dpkg: error processing /var/cache/apt/archives/xulrunner-1.9.1_1.9.1.7+nobinonly-0ubuntu0.9.10.1_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/rm/rm: cannot remove `/usr/lib/xulrunner-1.9.1.7/python/xpcom/__init__.pyo': No such file or directory
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Selecting previously deselected package xulrunner.
Unpacking xulrunner (from .../xulrunner_1.8.1.16+nobinonly-0ubuntu1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/xulrunner-1.9.1_1.9.1.7+nobinonly-0ubuntu0.9.10.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by iponeverything on 2010-01-09
just for the fun of it why don't you give it something to delete

```
sudo touch /usr/lib/xulrunner-1.9.1.7/python/xpcom/__init__.pyo
```

Then try the install again.

---

### Post by Exüberance on 2010-01-09
I don't have the **python** directory in  **/usr/lib/xulrunner-1.9.1.7**. I only have a directory called **components**.

I used **sudo apt-get remove xulrunner** and **sudo apt-get remove xulrunner-1.9-gnome-support***, which removed my xulrunner-1.9.1.7 directory, then tried reinstalling, but it didn't work.

The actual critical error seems to be in the following lines:
[B]Errors were encountered while processing:
 /var/cache/apt/archives/xulrunner-1.9.1_1.9.1.7+nobinonly-0ubuntu0.9.10.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]

Seems it's having problems unpacking the file.
(by the way, if you're wondering what's with the lines starting with **/rm/rm:**, that's just because I moved the file executed when using the **rm** command to a directory **/rm** I made, and replaced the original location of **rm** with a shell script that calls **/rm/rm $@ -I** so it has to ASK me before deleting a folder or more than 3 files at once.... somehow it seems to be bypassing it though since it never asked if I wanted to remove my xulrunner directory :/ Could that possibly somehow be causing a problem? I doubt it since all other packages install and uninstall perfectly fine.

---

### Post by Exüberance on 2010-01-10
H'uh. Turned out that actually was the problem. I'm not sure how that messed it up. Maybe it required rm to be an executable rather than a shell script. Anyways, problem solved.

---

