---
title: "Open Office 3.1"
date: 2009-10-04
forum: General Help
---

### Post by SteveB357 on 2009-10-04
I have searched this forum and the Open Office fora.  I got several different variants in the Open Office Lists.  I also Googled the question, and still haven't gotten it to work.

Is there any way to upgrade to Open Office 3.1 in Ubuntu.
The upgrade has some good features, particularly in the area of extensions, that will only work with 3.1.

It isn't on Synaptic.  When I try apt-get, it says that no such file or directory exists.  

Can someone give instructions, if this is possible at this time?

---

### Post by bobtfish on 2009-10-04
I haven't tried this, but a quick search found this site with instructions:
[http://webupd8.blogspot.com/2009/05/install-openoffice-31-in-ubuntu-jaunty.html]("http://webupd8.blogspot.com/2009/05/install-openoffice-31-in-ubuntu-jaunty.html")

---

### Post by Hagar Delest on 2009-10-05
Personally, I only install the official (Sun) version and it works fine: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by fooman on 2009-10-05
if your using intrepid or jaunty....this should work:

[http://ubuntuforums.org/showthread.php?t=987181](http://ubuntuforums.org/showthread.php?t=987181)

don't think they have the hardy packages anymore though. :(

---

### Post by scouser73 on 2009-10-05
Firstly, go to the OpenOffice website: [[COLOR="Red"]**OpenOffice.org**[/COLOR]]("http://download.openoffice.org/other.html") and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m19_native_packed-1_en-US.9420**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

---

### Post by snowpine on 2009-10-05
OpenOffice 3.1 will be standard in Ubuntu 9.10 Karmic, which will be released later this month. Ubuntu "lumps together" big updates into a new release every six months, rather than releasing major new updates as soon as they are available.

---

