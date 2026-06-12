---
title: "Software Install"
date: 2009-09-20
forum: General Help
---

### Post by jchambers on 2009-09-20
I am new to linux and I am trying to understand the porcess of installing a program. It is easy if I can locate a deb file as it is similar to windows and installs it however I am finding other things to install that are not packaged that way. Right now it is Azureus and it is aVuze_Installer.tar.bz2 file which opens by default with archive mgr - I have looked and it seems as if it is discouraged to install anything that is not already listed in the add/remove area and I need to compile this to install it. I searched differnt articles and I am not really getting this process so far. Please advise!

---

### Post by Zimmer on 2009-09-20
Azureus 3.1.1.0-4 is in the Universe repository and can be installed via the Synaptic package manager.

There are ways of installing packages from 'other' places but you should only need to resort to them if you desperately need a special build/very latest package/ or the application is not included in ANY Ubuntu repository .

[https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html)

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

see chapter 6

---

### Post by unmole on 2009-09-20
You don't need to find a .deb. If you are using ubuntu 9.04 it is already in the repos. Install it using Synaptic.
Click on system in your top panel then Administration then Synaptic Package Manager. It will ask you for your password. Then in the search box that appears type azureus. Right click on the azerus for the list and click mark for install then clcick apply.........

---

### Post by kostkon on 2009-09-20
You could check [this nice how-to]("http://www.psychocats.net/ubuntu/installingsoftware") on how to install software in Ubuntu.

---

### Post by unmole on 2009-09-20
Or simply open a terminal (Applications->Accesories->Terminal) and type..

sudo apt-get install azureus

Hit enter you will be asked for your password and you are on your way......

---

### Post by TobiDN on 2009-09-20
> **jchambers said:**
> I am new to linux and I am trying to understand the porcess of installing a program. It is easy if I can locate a deb file as it is similar to windows and installs it however I am finding other things to install that are not packaged that way. Right now it is Azureus and it is aVuze_Installer.tar.bz2 file which opens by default with archive mgr - I have looked and it seems as if it is discouraged to install anything that is not already listed in the add/remove area and I need to compile this to install it. I searched differnt articles and I am not really getting this process so far. Please advise!

Well, at least Azureus is in the Synaptic package manager (System - Adminstration - Synaptic, or simply "sudo apt-get azureus" in the terminal).
Some applications do require you to compile them for yourself, it shouldn't be too hard though. You can probably find a good guide with a google search.
Otherwise, there may be some notes on the installation in the folder.

---

### Post by kostkon on 2009-09-20
> **TobiDN said:**
> Some applications do require you to compile them for yourself,
Which ones?

---

### Post by jchambers on 2009-09-20
Thanks for the help - I used Synaptic and it works fine and I had already read the how to posted but I guess it just not make sense to me the first time - it is a new concept to have a online "store" of available software to me. Thanks very much!

---

### Post by dcraven on 2009-09-20
> **kostkon said:**
> Which ones?

hehe.. It's not really feasible to attempt compiling a list of these projects. :)

~djc

---

