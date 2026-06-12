---
title: "aptitude issues on armel system"
date: 2011-12-29
forum: General Help
---

### Post by hogman500 on 2011-12-29
ok i have been messing around with putting a Ubuntu distro on my android tablet i used a app Linux installer which did as it said in installing Linux. i chose Ubuntu 9.04 because i had used this version for several years on my computer. i got it installed and installed tight vnc and am running it vnc to a vnc viewer on my tablet so i can access the GUI. i am running iceWM.anyway this is my problem i forced several packages to install without proper dependencies specifically iceWM and its common files. it functions so i dont want to mess with is but now when i use aptitude it gives me errors on the dependencies and wont let me do anything else it gives me the solution of removing the iceWM but i dont want to do that i just want to keep using it the way it is.

anyway my ultimate question is is it possible to override these errors and make aptitude work anyway?    

all i want to do is install Firefox and a few other programs without errors constantly or at least force it to work.

also aptitude gave me issues to start with with libreadline5 i had to manually install it in order to get it to function i can manually do this for iceWM but would prefer not to.

thank you in advance for your insight

---

### Post by lisati on 2011-12-29
9.04 is past its end of life. If you want aptitude or apt-get to work, you'll have to redirect your sources.list file. See  [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) for more information.

---

### Post by thatguruguy on 2011-12-29
Ubuntu 9.04 is no longer supported, because it reached end of life a year ago.  You're trying to use aptitude to access repositories that don't exist.  The earliest version of Ubuntu you'll be able to find any support for is 10.04.

---

### Post by hogman500 on 2011-12-29
OK I can do the sources. List thing and I undedefame that it is old but all I want to do is get past the massive amount of errors so I can use it at all and i tried to fix the dependencies and it agravated the problem now instead of the error saying i wasb missing 5 dependencies it says i am missing like 20 it is not a sources problem its a problem of missing dependencies not related to aptitude giving so many errors apt-get and aptitude are unusable

So missing dependencies for iceWM not missing sources in sources.list

I would just like to bypass the error so i can use it and ignore the error



And just to mention i am running the newest version of ubuntu on my desktop

---

### Post by lisati on 2011-12-29
Are you saying that you already fixed your sources.list file? "Source" in this context does not refer to "source code" but the place that aptitude gets what it needs to fix dependencies, and because 9.04 is past its end of life, it won't be able to look in the default location.

apt-get and aptitude are most likely unusable because 9.04 has passed the end of its life, and to fix this the first thing you need to do is update your sources.list file as outlined in the link I gave earlier.

---

### Post by hogman500 on 2011-12-29
I know about the /etc/apt/sources.list and i have installed stuff through aptitude before so I know it is not the problem 

Here you go so you can see what I me an 

Root@Galoula-ARMEL:/# aptitude install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No candidate version found for firefox
No candidate version found for firefox
The following packages are BROKEN:
  icewm-gnome-support libesd0 libgail18 libgcc1 libgconf2-4 libgtk2.0-0
  libstartup-notification0
The following packages will be REMOVED:
  esound-clients{u} esound-common{u} libcups2{u} ttf-dejavu{u} ttf-dejavu-extra{u}
0 packages upgraded, 0 newly installed, 5 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 6615kB will be freed.
The following packages have unmet dependencies:
  libgail18: Depends: libgtk2.0-0 (= 2.16.1-0ubuntu2) but 2.20.1-2 is installed.
  libgconf2-4: Depends: libxml2 (>= 2.7.4) but 2.6.32.dfsg-5ubuntu4.2 is installed.
               Depends: gconf2-common (>= 2.28) but 2.26.0-0ubuntu1 is installed.
  libgcc1: Depends: gcc-4.4-base (= 4.4.5-8) which is a virtual package.
  libstartup-notification0: Depends: libxcb-atom1 (>= 0.3.3) which is a virtual package.
                            Depends: libxcb-aux0 (>= 0.3.3) which is a virtual package.
                            Depends: libxcb-event1 (>= 0.3.3) which is a virtual package.
  icewm-gnome-support: Depends: libgnome-desktop-2-17 (>= 1:2.29.4) but 2.30.2-2 is installed.
  libesd0: Depends: esound-common (= 0.2.41-8) but it is not installable
  libgtk2.0-0: Depends: libatk1.0-0 (>= 1.29.3) but 1.26.0-0ubuntu2 is installed.
               Depends: libcups2 (>= 1.4.0) but it is not installable
               Depends: libgcrypt11 (>= 1.4.2) but 1.4.1-2ubuntu1 is installed.
               Depends: libgnutls26 (>= 2.7.14-0) but 2.4.2-6 is installed.
               Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) which is a virtual package.
               Depends: libjpeg62 (>= 6b1) but 6b-14 is installed.
open: 1; closed: 0; defer: 0; conflict: 1                                              .Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  icewm-gnome-support libesd0 libgail18 libgcc1 libgconf2-4 libgtk2.0-0
  libstartup-notification0
The following packages will be REMOVED:
  esound-clients{u} esound-common{u} libcups2{u} ttf-dejavu{u} ttf-dejavu-extra{u}
0 packages upgraded, 0 newly installed, 5 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 6615kB will be freed.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  libgail18: Depends: libgtk2.0-0 (= 2.16.1-0ubuntu2) but 2.20.1-2 is installed.
  libgconf2-4: Depends: libxml2 (>= 2.7.4) but 2.6.32.dfsg-5ubuntu4.2 is installed.
               Depends: gconf2-common (>= 2.28) but 2.26.0-0ubuntu1 is installed.
  libgcc1: Depends: gcc-4.4-base (= 4.4.5-8) which is a virtual package.
  libstartup-notification0: Depends: libxcb-atom1 (>= 0.3.3) which is a virtual package.
                            Depends: libxcb-aux0 (>= 0.3.3) which is a virtual package.
                            Depends: libxcb-event1 (>= 0.3.3) which is a virtual package.
  icewm-gnome-support: Depends: libgnome-desktop-2-17 (>= 1:2.29.4) but 2.30.2-2 is installed.
  libesd0: Depends: esound-common (= 0.2.41-8) but it is not installable
  libgtk2.0-0: Depends: libatk1.0-0 (>= 1.29.3) but 1.26.0-0ubuntu2 is installed.
               Depends: libcups2 (>= 1.4.0) but it is not installable
               Depends: libgcrypt11 (>= 1.4.2) but 1.4.1-2ubuntu1 is installed.
               Depends: libgnutls26 (>= 2.7.14-0) but 2.4.2-6 is installed.
               Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) which is a virtual package.
               Depends: libjpeg62 (>= 6b1) but 6b-14 is installed.
Resolve these dependencies by hand? [N/+/-/_/:/?]

Don't want to fix just get around the error

---

### Post by hogman500 on 2011-12-29
Tried that tutorial in the link and when I do apt-get update it gives 404 not found errors on every source so that doesn't work an drag would that even work on my system I am armel running in parallel with android on a tablet

---

### Post by hogman500 on 2011-12-30
Ok i fixed it thank you for your help. I had to manually install 15 dependencies with dpkg --force-all -i and it fixed enough dependency problems for apt-get -f install to figure it out without killing my iceWM.

Also my sources.list file seems ok it is a new install only 3 days old already had the sources.list adjusted for it being outdated. And i now have a running version of ubuntu on my tablet. 

Thanks for everyones help.

---

