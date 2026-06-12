---
title: "FGLRX broken"
date: 2011-08-11
forum: General Help
---

### Post by Bart92 on 2011-08-11
I was installing the ATI driver in Ubuntu 11.04 x64 (again) from the AMD website but the installation freezes so i aborted the installation

Now i am having some problems with the fglrx installation the package is broken but i can't restore it in recovery mode by choosing restore broken packages i have also tried a couple of commands.


sudo apt-get install fglrx : doesn't work
[B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
/var/cache/apt/archives/fglrx_2%3a8.840-0ubuntu4_amd64.deb[/B]

sudo apt-get autoremove fglrx doesn't work
[B]
Package fglrx is not installed[/B]

sudo apt-get -f install fglrx : doesn't work

Synaptic package manager doesn't work either

Update manager gives me a error too

The following packages have unmet dependencies:

fglrx-amdcccle: Depends: fglrx but it is not installed
                Depends: libqtcore4 (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is installed
                Depends: libqtgui4 (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is installed

pleas help ....

thanks

---

### Post by Bart92 on 2011-08-11
Anyone ?>

---

