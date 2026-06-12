---
title: "New Version Of Openoffice.org"
date: 2009-08-12
forum: General Help
---

### Post by accooper on 2009-08-12
I just downloaded the newest version of Openoffice.org Version 3.1.0.  I was wondering how I would install this.

The file I downloaded is called:

OOo_3.1.0_LinuxIntel_install_en-US-deb.tar.gz

Any help here?

Andrew

---

### Post by scouser73 on 2009-08-12
Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the Linux **.deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m11_native_packed-4_en-US.9399**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m11_native_packed-4_en-US.9399** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9393_all.deb**

Once you've done that you'll find OpenOffice 3.1.0 in Office.

---

