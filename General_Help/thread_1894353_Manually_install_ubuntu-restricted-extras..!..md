---
title: "Manually install ubuntu-restricted-extras..?!\."
date: 2011-12-12
forum: General Help
---

### Post by koohyar on 2011-12-12
I've set up an Ubuntu box in the PC at home, but there's not a sophisticated enough internet connection available there!
So I was thinking maybe I could manually bundle the  necessary ".deb" files (like gstreamer-ffmpeg and so forth) from my laptop (say from /var/cache/apt/archives) and install what installing ubuntu-restricted-extra package would. But the problem is each of them has some dependencies of their own. So I guess I need a recursive hierarchy of the 10 packages that restricted-extra installs.
If I have the hierarchical packages, I thought maybe I could use something like a  dpkg -i *.deb or maybe add a file to /etc/apt/sources.list and using apt-get...
But that's just the main idea and I don't know how to apply it! :)
Would appreciate any help
Thank you\.

---

### Post by zero2xiii on 2011-12-12
Hay,

Have a look at "aptonCD" application, it might serve your needs.

I really wish ubuntu will package the restricted-extras package with ubuntu as an option to install. This is propably the MOST installed package in the repro.

Cherz

---

### Post by gandaran on 2011-12-12
> **koohyar said:**
> I've set up an Ubuntu box in the PC at home, but there's not a sophisticated enough internet connection available there!
So I was thinking maybe I could manually bundle the  necessary ".deb" files (like gstreamer-ffmpeg and so forth) from my laptop (say from /var/cache/apt/archives) and install what installing ubuntu-restricted-extra package would. But the problem is each of them has some dependencies of their own. So I guess I need a recursive hierarchy of the 10 packages that restricted-extra installs.
If I have the hierarchical packages, I thought maybe I could use something like a  dpkg -i *.deb or maybe add a file to /etc/apt/sources.list and using apt-get...
But that's just the main idea and I don't know how to apply it! :)
Would appreciate any help
Thank you\.
get all the packages from  /var/cache/apt/archives on a flash drive and put them on the same /var/cache/apt/archives directory on the other ubuntu PC then open software center to install ubuntu-restricted-extras normally.
(run **sudo apt-get update** before trying the install)

---

### Post by koohyar on 2011-12-12
Thank you very much!
I'll give these a try!\.

---

### Post by koohyar on 2011-12-16
I also found this charming application: remastersys!
Since the installation on my PC was a brand new one, I just replaced it with the custom image I made from laptop's oneiric and...everything is in its place! :)
But for further updates and package installation, aptOnCD or manually copying the deb files to the apt/archives folder should be more handy\.

---

