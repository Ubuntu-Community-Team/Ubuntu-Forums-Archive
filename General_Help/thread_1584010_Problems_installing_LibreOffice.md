---
title: "Problems installing LibreOffice"
date: 2010-09-28
forum: General Help
---

### Post by K. Alan Eister on 2010-09-28
I'm running Ultimate Edition 2.5 64-bit on a Sony Vaio VGN-FW520F.  I am trying to install the LibreOffice beta.  I obtained the *.tar.gz package and went through the terminal line of sudo apt-get install *route to package*, and got the following errors:

E: Malformed line 56 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.

Lines 55-57 of my source list look like this:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) karmic main

Anyone have any advice on how to correct the error?  Or, at least, an alternative route of installing the *.tar.gz file?

---

### Post by coffeecat on 2010-09-28
A tar.gz file is a source code file and you cannot install it with apt-get. You have to compile it. I would advise waiting a day or two by which time a .deb file (which is what you need for Debian derivatives such as Ubuntu) should be available. Simply download the .deb file and double-click on it to install it.

I don't know why you are getting the malformed line error - those lines look OK to me. I suggest you post the whole of your sources.list file. Please enclose them in [noparse]```

```[/noparse] tags.

---

### Post by gradinaruvasile on 2010-09-28
Here:

[http://download.documentfoundation.org/libreoffice/testing/LO_3.3.0-beta1_Linux_x86_install-deb_en-US.tar.gz.mirrorlist](http://download.documentfoundation.org/libreoffice/testing/LO_3.3.0-beta1_Linux_x86_install-deb_en-US.tar.gz.mirrorlist)

Are the debs and stuff. First unpack the tar.gz then install all the .debs from the DEBS and DEBS/desktop-integration folders (in this order).

The command is

sudo dpkg -i *.deb

in a terminal in the folder with the .deb files.

---

### Post by GrokIt on 2010-09-28
Thanks gradinaruvasile!  I got the rpm tar.gz from the site and was about to alien all the packages when I decided to check here first.  Saved me a bit of trouble. :-\"

---

### Post by coffeecat on 2010-09-28
Whoops: correction. I'd forgotten that the erstwhile Open Office people had a habit of wrapping .debs and .rpms in tar.gz tarballs. Listen to gradinaruvasile.

---

### Post by SGAZ on 2010-09-28
@ gradinaruvasile  

THANKS !

I don't install straight from debs that often and staring at a whole folder full of them threw me for a loop.  All up and running now.

Much Appreciated!

---

### Post by opodaniel on 2010-09-29
Is it possible to install just Writer and Calc? 

I folow the GradinaruleVasile instruction and it installed the whole package which for me is a waste of space since I don't use them. If I remove them from Ubuntu Software Center I cannot use Writer and Calc no more.

I tried another strategy: I removed all the deb package that I don't need , the result being a working Writer and Calc but Ubuntu Software Center see some errors in package index and won't do any other operation until it removes libreoffice3.

By the way I am new in Linux World . 

The link for 64-bit version of LibreOffice deb package is [http://mirror.lupaworld.com/tdf/libreoffice/testing/LO_3.3.0-beta1_Linux_x86-64_install-deb_en-US.tar.gz](http://mirror.lupaworld.com/tdf/libreoffice/testing/LO_3.3.0-beta1_Linux_x86-64_install-deb_en-US.tar.gz)

---

### Post by brian_martin on 2010-09-29
Thanks for the guidance above. it worked.

When I opened Writer I got a message about needing a jre. There was no statement about what to use. In Synaptic I searched for jre and selected openjdk-6-jre and that pulled in a number of other packages.

When I opened an existing database I found the java version was Sun 1.6.0_18. The Sun Report Builder was dropped and I had to install a new version that was older than the one I had been using and aspects of it did not work eg after an edit I could not execute and parts of the report were "dropped".

Brian

---

### Post by scouser73 on 2010-09-29
As LibreOffice is at the third beta stage it shouldn't be used in production environments but if you wish, it can be installed nonetheless.

**1** - Download LibreOffice from: [[COLOR="Red"]**LibreOffice Downloads**[/COLOR]]("http://download.documentfoundation.org/libreoffice/testing/")

**2** - Extract the file to **~/Desktop**

**3** - Rename the file to **libreoffice**

**4** - Open Terminal and enter this command: **> sudo dpkg -i ~/Desktop/libreoffice/DEBS/*.deb**

**5** - Then enter the following command into Terminal: **> sudo dpkg -i ~/Desktop/libreoffice/DEBS/desktop-integration/libreoffice3.3-debian-menus_3.3-9526_all.deb**

You have now successfully installed LibreOffice.

---

### Post by meho_r on 2010-10-01
Those who have it installed, what theme is it using? I got menus/windows with Win98-ish look (I guess, it's default theme for OOo and LibreOffice too), which means that Gnome integration failed for some reason. Any ideas?

---

### Post by frogotronic on 2010-10-02
> **opodaniel said:**
> Is it possible to install just Writer and Calc? 

I folow the GradinaruleVasile instruction and it installed the whole package which for me is a waste of space since I don't use them. If I remove them from Ubuntu Software Center I cannot use Writer and Calc no more.

I tried another strategy: I removed all the deb package that I don't need , the result being a working Writer and Calc but Ubuntu Software Center see some errors in package index and won't do any other operation until it removes libreoffice3.

By the way I am new in Linux World . 

The link for 64-bit version of LibreOffice deb package is [http://mirror.lupaworld.com/tdf/libreoffice/testing/LO_3.3.0-beta1_Linux_x86-64_install-deb_en-US.tar.gz](http://mirror.lupaworld.com/tdf/libreoffice/testing/LO_3.3.0-beta1_Linux_x86-64_install-deb_en-US.tar.gz)

Hi Daniel,

  Generally no...because they all have inter-dependencies.  Better strategy is to install everything, and then try and uninstall what you don't want.

- CH

---

### Post by bedbug on 2010-10-03
[https://launchpad.net/ubuntu/+archive/primary/+files/libglitz1_0.5.6-1build1_i386.deb]("https://launchpad.net/ubuntu/+archive/primary/+files/libglitz1_0.5.6-1build1_i386.deb")

sudo dpkg -i libglitz1_0.5.6-1build1_i386.deb

After Installing, Start
 
libreoffice -writer

Any Change?!

---

### Post by meho_r on 2010-10-09
> **bedbug said:**
> [https://launchpad.net/ubuntu/+archive/primary/+files/libglitz1_0.5.6-1build1_i386.deb]("https://launchpad.net/ubuntu/+archive/primary/+files/libglitz1_0.5.6-1build1_i386.deb")

sudo dpkg -i libglitz1_0.5.6-1build1_i386.deb

After Installing, Start
 
libreoffice -writer

Any Change?!

Thanks a lot for the info, that solves the integration problem.

---

### Post by isantop on 2010-10-13
For 64-bit users:

[http://ftp.kaist.ac.kr/ubuntu/pool/universe/g/glitz/libglitz1_0.5.6-1_amd64.deb](http://ftp.kaist.ac.kr/ubuntu/pool/universe/g/glitz/libglitz1_0.5.6-1_amd64.deb)

sudo dpkg -i libglitz1_0.5.6-1build1_amd64.deb

---

