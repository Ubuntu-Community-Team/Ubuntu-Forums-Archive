---
title: "Install OpenOffice 3.1.1"
date: 2009-08-31
forum: General Help
---

### Post by scouser73 on 2009-08-31
Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m19_native_packed-1_en-US.9420**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

---

### Post by chriskin on 2009-08-31
> **scouser73 said:**
> Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m19_native_packed-1_en-US.9420**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

shouldn't that be in tutorials instead of here?
I would prefer the "add ppa repository and update" way

---

### Post by balaknair on 2009-08-31
Or better still, if you're using Jaunty, wait a little bit and use the Open Office PPA
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

They currently have OOo 3.1.0 but should have 3.1.1 ready soon(being prepared).
It's much better to have the repositories, imo. Using the downloaded debs can(and for many like me, has) create major problems with Java and Gnome dependencies.

BTW, does anyone know for certain if Karmic will have OOo 3.1.0 or 3.1.1. I guess that would depend on the GOOo folks.

---

### Post by Hagar Delest on 2009-09-02
The ppa version can cause troubles, users have experienced a lot of problems with first versions last year. Better use the official version (Sun) IMHO. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) I've never experienced any problem with Java or Gnome or XFCE dependencies.

---

