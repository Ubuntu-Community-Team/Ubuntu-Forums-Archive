---
title: "Ubuntu 7.10 - How to upgrade OpenOffice to 2.3.1"
date: 2009-11-10
forum: General Help
---

### Post by keenboy on 2009-11-10
Hi,

I have got some bugs with OpenOffice which people say are fixed by upgrading to OpenOffice 2.3.1 (I am running 2.3.0).

I would like to upgrade using apt if I can because it is an ubuntu package.

How can I do this?

I don't want to upgrade the distro, just OpenOffice.

Thanks,

---

### Post by snowpine on 2009-11-10
Hi Keenboy, since Canonical no longer supports 7.10, your best bet is probably to download and install the latest OpenOffice directly from openoffice.org.

---

### Post by scouser73 on 2009-11-10
> **keenboy said:**
> Hi,

I have got some bugs with OpenOffice which people say are fixed by upgrading to OpenOffice 2.3.1 (I am running 2.3.0).

I would like to upgrade using apt if I can because it is an ubuntu package.

How can I do this?

I don't want to upgrade the distro, just OpenOffice.

Thanks,

Firstly, go to the OpenOffice website:[[COLOR="Red"]**Download OpenOffice.org**[/COLOR]]("http://download.openoffice.org/other.html#en-US") and download the **Linux .deb** file.

**1 -** Remove the existing version of OpenOffice if you wish with this command: > **sudo apt-get remove openoffice*.***

**2 -** Extract the .deb file, > **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** 

**3 -** You'll now see a file called **OOO310_m19_native_packed-1_en-US.9420**

**4 -** Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: > **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

**5 -** Then paste this command: > **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

---

### Post by tunchi_1939 on 2009-11-12
Hi Scouser73: I want to upgrade to OpenOffice 3.1.1 in Ubuntu 8.04.
Is it possible to follow the method you recomended for Ubuntu 8.04?
Thank you very much for your advise.
Sorry for my english.
tunchi_1939 from Lima, Peru, South America.

---

### Post by scouser73 on 2009-11-12
Yes, those instructions will work for Ubuntu 8.04.

---

