---
title: "Google Earth"
date: 2010-11-15
forum: General Help
---

### Post by petersull on 2010-11-15
Hi,

I am trying to get google earth installed.

I have tried all the different methods on the following website...

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

but cannot get it to install.

Can anyone give me specific instructions that will work with Ubuntu 10.10 please.

---

### Post by ratcheer on 2010-11-15
Google Earth installation can be a real pain. The best method I have found is to find and delete all the Google Earth stuff (especially config files and little hidden folders), then do a fresh install of GE. That worked for me. Specifically, you must remove the following from your home directory:

.googleearth
.config/Google



I hope this helps.

Tim

---

### Post by cariboo on 2010-11-15
Probably the easiest way to install Googleearth is to enable the Medibuntu repositories, then install it using the Software center or Synaptic Package Manager.

To enable the Medibuntu repositories go [here]("https://help.ubuntu.com/community/Medibuntu"). Once you have done that just search for googleearth using the applications mentioned above.

---

### Post by netz1010 on 2010-11-21
Please follow the link for the installation instructions.
[http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)

After you installed google earth if you start it it will probably start and shut down.
Please follow these steps to workaround.

1. Disconect from the net
2. Start google earth
3. go to tools/options general tab and uncheck box where it says show start up tips.
4.Exit
5.Connect to the net

It should work fine now.

---

### Post by Peter AB on 2010-11-23
Did not work for me. Google Earth appears in the list, (UBUNTU SOFTWARE CENTRE) but when asked to Instal it, it replies "There is no software package called "Googleearth" in your current software sources".
I can instal other Google progams!
Any further help please!

---

### Post by sarin_cv on 2010-11-23
have u tried this?

[http://www.howtoforge.com/how-to-install-google-earth-on-ubuntu-10.10](http://www.howtoforge.com/how-to-install-google-earth-on-ubuntu-10.10)

---

### Post by gandaran on 2010-11-23
> **Peter AB said:**
> Did not work for me. Google Earth appears in the list, (UBUNTU SOFTWARE CENTRE) but when asked to Instal it, it replies "There is no software package called "Googleearth" in your current software sources".
I can instal other Google progams!
Any further help please!
after installing this package in ubuntu software centre you have to run in terminal (this package is only a script to build a .deb package not install google earth)
```
make-googleearth-package --force
```
then wait till it downloads the google earth bin from google earth website and build a .deb package in your hone user directory, it will take some time to build the package, when you have the .deb package ready just click it to install.

there is also another way to install google earth easily in package manager, add the super os repository then you can find google earth ready to install in package manager.
if you are interested download [this package]("http://hacktolive.org/files/Super_OS_10.04_repo_v0.3.1_all.deb") and install it, it will add the super os repository to software sources.
update the software package list then look for google earth in package manager and install it

---

### Post by Peter AB on 2010-11-23
Thaks, I finally solved the problem and it is working now (after a fashion. The fonts are all squashed, but still useable. My problem seems to have been that I was only putting googleearth.deb in the last line instead of the FULL form 'googleearth_<the rest of the long string of numbers>.deb Bothe optiond appeared to be there in the teminal!
Any way, many thanksd for all the help to all!
Peter AB

---

### Post by wheelie207 on 2010-11-25
I had used the ubuntu software center and followed what info on installing googleearth on ubuntu 10.10 and I found out that it may have installed, but I found it did not install 31 different lib files. Without those lib files it will not run except for the very start of it and closes because of the missing files.
I'm currently looking for the files so I can install the files and then reinstall googleearth and maybe I will be able to run the program.

---

