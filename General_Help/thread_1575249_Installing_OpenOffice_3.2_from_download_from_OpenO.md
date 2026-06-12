---
title: "Installing OpenOffice 3.2 from download from OpenOffice.org"
date: 2010-09-15
forum: General Help
---

### Post by e24ohm on 2010-09-15
I am having problems installing the *OOO_3.2.1_Linux_x86_install-deb_en-US.tar.gz* install package from **openoffice.org**. When I unpack the *tar.gz *file, I get another folder labeled *OOO320_m18_native_packed-1_en-US.9502*, which as a folder named **DEBS** that has number of .deb files.

How do I install the mentioned file or files? I would like to use the download for installation, so I can get the updated version of OpenOffice, and not use the Ubuntu repository.

Thanks.

---

### Post by philinux on 2010-09-15
> **e24ohm said:**
> I am having problems installing the *OOO_3.2.1_Linux_x86_install-deb_en-US.tar.gz* install package from **openoffice.org**. When I unpack the *tar.gz *file, I get another folder labeled *OOO320_m18_native_packed-1_en-US.9502*, which as a folder named **DEBS** that has number of .deb files.

How do I install the mentioned file or files? I would like to use the download for installation, so I can get the updated version of OpenOffice, and not use the Ubuntu repository.

Thanks.

This is a better way. [http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html](http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html)

---

### Post by e24ohm on 2010-09-15
Hey thank for the link; however, how is the install completed from the openoffice.org website? I want to be able to complete the install at least once to learn how to do it.

In addtion, I have already installed Thunderbird 3.1 from the official download, and installed the application into the */opt *location, so I am pretty excited to learn how to install OpenOffice from the .deb packages.

thanks for the help!!
Cheers!!!

---

### Post by snowpine on 2010-09-15
.deb files can be installed in (at least) two different ways:

1. Double-click on the icon in your file manager to open the file with Gdebi

2. From the terminal, use 'sudo dpkg -i nameoffile.deb' (the -i means "install")

You can use wildcards so for example

```
cd /folder/where/the/debs/are
sudo dpkg -i *.deb
```

Hope that makes sense!

Personally I would use the stable, tested, and trusted OpenOffice from the Ubuntu repositories, but sometimes it is a fun learning experience to try something different. Good luck! :)

---

### Post by scouser73 on 2010-09-15
Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the Linux .deb file to your desktop

Once you have done that, extract the .deb file, 

OOo_3.2.1_LinuxIntel_install_en-US_deb.tar.gz

Then you'll see a file called OOO320_m18_native_packed-1_en-US.9502

Remove the existing version of OpenOffice with this command: 

> sudo apt-get remove openoffice*.*

Then paste this command:

> sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/*.deb

Then paste this command: 

> sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9502_all.deb

Once you've done that you'll find OpenOffice 3.2.1 in Office.

---

### Post by e24ohm on 2010-09-15
> **scouser73 said:**
> Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the Linux .deb file to your desktop

Once you have done that, extract the .deb file, 

OOo_3.2.1_LinuxIntel_install_en-US_deb.tar.gz

Then you'll see a file called OOO320_m18_native_packed-1_en-US.9502

Remove the existing version of OpenOffice with this command: 



Then paste this command:



Then paste this command: 



Once you've done that you'll find OpenOffice 3.2.1 in Office.

hey thanks...that did the trick...

I like the last part...In Fedora I had to play around with the */usr/share/applications* and build all the *.desktop *files.

---

