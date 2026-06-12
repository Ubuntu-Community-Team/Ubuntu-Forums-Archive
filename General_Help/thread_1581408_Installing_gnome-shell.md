---
title: "Installing gnome-shell"
date: 2010-09-24
forum: General Help
---

### Post by Chethan S on 2010-09-24
Today I watched a video about GNOME 3.0 on  YouTube and wanted to install it on ubuntu 10.04. But when I proceed to  install gnome-shell I get an error about the xulrunner dependency. I  searched on web and found that adding some ritcoz ppa helps but it  resulted in same error. The command executed by me and the output is  given below. Can anyone suggest a solution.


> chethan@chethan-desktop:~$ sudo aptitude install gnome-shell
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages are BROKEN:
  libgjs0
The following NEW packages will be installed:
  gir1.0-atk-1.0{a} gir1.0-clutter-1.0{a} gir1.0-freedesktop{a}
  gir1.0-glib-2.0{a} gir1.0-gtk-2.0{a} gir1.0-mutter-2.28{a}
  gir1.0-pango-1.0{a} gnome-shell xserver-xephyr{a}
0 packages upgraded, 10 newly installed, 0 to remove and 22 not upgraded.
Need to get 3,370kB of archives. After unpacking 7,721kB will be used.
The following packages have unmet dependencies:
  libgjs0: Depends: xulrunner-1.9.2 (<= 1.9.2.9~) but 1.9.2.10+build1+nobinonly-0ubuntu0.10.04.1 is installed.
The following actions will resolve these dependencies:
 Keep the following packages at their current version:
gnome-shell [Not Installed]
libgjs0 [Not Installed]
 Score is -9868
 Accept this solution? [Y/n/q/?]
 



 I answered Y as I did not want to face problems later.

---

### Post by andrewthomas on 2010-09-24
Have you looked through this thread?

[http://ubuntuforums.org/showthread.php?t=1476241&highlight=gnome-shell](http://ubuntuforums.org/showthread.php?t=1476241&highlight=gnome-shell)

---

### Post by Chethan S on 2010-09-26
I looked at the thread. It had three options:

[LIST=1]
[*]To install gnome-shell from the repository - This was not possible due to the dependency problem.
[*]To use ritcoz ppa - The error which appears is same as the one for above option     > The following packages have unmet dependencies:
  gnome-shell: Depends: libgjs0 but it is not going to be installed
[*]Building from source - This was very lengthy process, it wanted to download some 23 packages from gnome git but resulted in a series of errors after downloading 15 odd packages. Again using the options for solving the problems in the post did not help me.
[/LIST]
Is there any other way out to install gnome 3?

---

### Post by Chethan S on 2010-09-27
I guess now the dependency issues are solved. I could install gnome-shell without any issues today.

---

