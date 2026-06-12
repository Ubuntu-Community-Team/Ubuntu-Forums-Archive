---
title: "Xgl + compiz + KDE with borders and nautilus file manager begginers guide."
date: 2006-04-03
forum: General Help
---

### Post by Knowledge2012 on 2006-04-03
You need KDE for this. To get kde:
1) Go to synaptic, CNTL+F or search for KDE, install.

2) Follow this guide (does not work with 64bit+x200m combination):
[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916) - Should probably restart. Log into gnome and go to the next step.

3)Edit ~/.Xsession. (sudo gedit ~/.Xession) in console. replace "kde-window-decorator" with "gnome-window-decorator" if not already done, & exec "gnome-session" to "startkde" if not already done.

4) Because konqueror wont work with KDE and xgl+compiz right now (still in development) you will need to uninstall konqueror, this should allow the system to automatically use nautilus, the file manager that comes with gnome.

5) Now log out, and change your session to KDE, log in, MAKE DEFAULT. Now log out, log into "Default", should be number 2, and vawala, you should have A working KDE+nautilus+borders.

If you would like more Dapper repositorys, i aquired this list i dont remmber where i got it, but i know it was on the ubuntu forums i believe.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the ‘universe’
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the ‘backports’
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

## Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

sudo apt-get update           
sudo apt-get upgrade


good luck.

---

### Post by Al3xanR0 on 2006-04-03
Thanks, I'm all over it!

---

