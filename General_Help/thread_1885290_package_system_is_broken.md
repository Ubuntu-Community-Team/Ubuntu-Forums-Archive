---
title: "package system is broken"
date: 2011-11-22
forum: General Help
---

### Post by jonbjoseph on 2011-11-22
I'm running 32bit desktop version of Ubuntu 11.10.
Today I ran the update manager and my system froze, which caused me to do a hard restart.
After restarting, I'm unable to run the package manager.  There are unmet dependencies and my package system is probably in an inconsistent state that I don't know how to recover from.  (How do you remove 3rd party repositories?) The following are a couple of things I tried and the corresponding responses.

Any help would be greatly appreciated.
Thanks,
Jonathan


1) apt-get -f upgrade 

When running 'apt-get -f upgrade', I get the following messages. I get the same messages when running 'apt-get install -f'

Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_8.0+build1-0ubuntu0.11.10.3_i386.deb
 /var/cache/apt/archives/libgs9-common_9.04~dfsg-0ubuntu11.1_all.deb
 /var/cache/apt/archives/libreoffice-writer_1%3a3.4.4-0ubuntu1_i386.deb
 /var/cache/apt/archives/libreoffice-gtk_1%3a3.4.4-0ubuntu1_i386.deb
 /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb
 /var/cache/apt/archives/libreoffice-core_1%3a3.4.4-0ubuntu1_i386.deb
 /var/cache/apt/archives/gnome-control-center-data_1%3a3.2.2-0ubuntu1_all.deb
 /var/cache/apt/archives/gnome-control-center_1%3a3.2.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)




2) Clicking on red circle at top of screen

At the top of my desktop, I clicked on a red-circle (with a white line) and it displayed the following message and 'Install All Updates' menu option:

An error occurred, please run Package Manager from the right click menu or apt-get in a terminal to see what is wrong.  The error message was: 'Error BrokenCount > 0'. This usually means that your installed packages have unmet dependencies.

I clicked on the 'Install All Updates' menu option and got the following error:
The package system is broken
Check if you are using third party repositories.  If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Details:
The following packages have unmet dependencies:
firefox-globalmenu: Depends: firefox (= 8.0+build1-0ubuntu0.11.10.3) but 7.0.1+build1+nobinonly-0ubuntu2 is installed
libgs9: Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is installed
        Depends: libgs9-common (= 9.04~dfsg-0ubuntu11.1) but 9.04~dfsg-0ubuntu11 is installed
libreoffice: Depends: libreoffice-core (= 1:3.4.4-0ubuntu1) but 1:3.4.3-3ubuntu2 is installed
libreoffice-base: Depends: libreoffice-core (= 1:3.4.4-0ubuntu1) but 1:3.4.3-3ubuntu2 is installed
                  Depends: libreoffice-base-core (= 1:3.4.4-0ubuntu1) but 1:3.4.4-0ubuntu1 is installed
                  Depends: libhsqldb-java (< 1.8.1~) but 1.8.0.10-9ubuntu1 is installed
libreoffice-base-core: Depends: libreoffice-core (= 1:3.4.4-0ubuntu1) but 1:3.4.3-3ubuntu2 is installed
libreoffice-calc: Depends: libreoffice-core (= 1:3.4.4-0ubuntu1) but 1:3.4.3-3ubuntu2 is installed
                  Depends: libreoffice-base-core (= 1:3.4.4-0ubuntu1) but 1:3.4.4-0ubuntu1 is installed
libreoffice-draw: Depends: libreoffice-core (= 1:3.4.4-0ubuntu1) but 1:3.4.3-3ubuntu2 is installed
libreoffice-gnome: Depends: libreoffice-core (= 1:3.4.4-0ubuntu1) but 1:3.4.3-3ubuntu2 is installed
libreoffice-impress: Depends: libreoffice-core (= 1:3.4.4-0ubuntu1) but 1:3.4.3-3ubuntu2 is installed
                     Depends: libreoffice-draw (= 1:3.4.4-0ubuntu1) but 1:3.4.4-0ubuntu1 is installed
libreoffice-l10n-en-gb: libreoffice-l10n-en-za: libreoffice-math: Depends: libreoffice-core (= 1:3.4.4-0ubuntu1) but 1:3.4.3-3ubuntu2 is installed
                  Depends: ttf-opensymbol (>= 2:2.4.3~) but 2:2.4.3+LibO3.4.4-0ubuntu1 is installed
libreoffice-writer: Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.4.3-3ubuntu2 is installed
                    Depends: libreoffice-base-core (= 1:3.4.3-3ubuntu2) but 1:3.4.4-0ubuntu1 is installed
python-uno: Depends: libreoffice-core (= 1:3.4.4-0ubuntu1) but 1:3.4.3-3ubuntu2 is installed
            Depends: python (< 2.8) but 2.7.2-7ubuntu2 is installed

---

### Post by jonbjoseph on 2011-11-22
The problem appears to be fixed.

I restarted ubuntu (again), ran 'sudo apt-get install -f' and everything ran as expected with no errors at all. Then I ran 'sudo apt-get upgrade' and again, everything ran as expected with no errors.

Thanks.
Jonathan

---

### Post by Foxheadz on 2011-11-22
"Check if you are using third party repositories. If so disable them, since they are a common source of problems." 
Have you tried disabling your ppa(s) and trying again?

---

### Post by jonbjoseph on 2011-11-22
Foxheadz,

Disabling 3rd party repositories was my next step.  However, I don't know how to do that and don't know how to disable ppas.  Clearly, I need to know how to manage the repositories. I plan to close this knowledge gap this weekend.

Thanks for your advice,
Jonathan

---

### Post by Foxheadz on 2011-11-22
Well open the software center then go to edit>software sources> and there should be like a "other" or "third party" tab with all the ppa's you added, just uncheck the box next to them and run ```
sudo apt-get update
```
And then retry upgrading your software

---

### Post by jonbjoseph on 2011-11-27
Foxheadz, thank you for your help on locating the 3rd party software sources.

---

### Post by richpob on 2012-01-02
I changed the Ubuntu software sources from "Main Server" to "Server for United State"

I'v fixed the problem

---

