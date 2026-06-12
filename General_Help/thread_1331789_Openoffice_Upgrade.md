---
title: "Openoffice Upgrade"
date: 2009-11-19
forum: General Help
---

### Post by anchorschmidt on 2009-11-19
I'm using Jaunty right now because Karmic doesn't work well on my hardware. I have Openoffice 3.01. I tried to use the Openoffice scribblers PPA to upgrade to 3.1.1 but it didn't work. I think that the PPA no longer supports Jaunty see link
 [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
so this tutorial [http://www.ubuntu-inside.me/2009/05/openoffice-31-for-ubuntu.html](http://www.ubuntu-inside.me/2009/05/openoffice-31-for-ubuntu.html) 
doesn't work anymore

How can I upgrade my Openoffice? I need to make anti-aliased graphs for my Physics assignment because it has to be very precise.

---

### Post by scouser73 on 2009-11-19
Firstly, go to the OpenOffice website:[[COLOR="Red"]**Download OpenOffice.org**[/COLOR]]("http://download.openoffice.org/other.html#en-US") and download the **Linux .deb** file.

**1 -** Remove the existing version of OpenOffice if you wish with this command: > **sudo apt-get remove openoffice*.***

**2 -** Extract the .deb file, > **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** 

**3 -** You'll now see a file called **OOO310_m19_native_packed-1_en-US.9420**

**4 -** Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: > **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

**5 -** Then paste this command: > **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

---

### Post by anchorschmidt on 2009-11-20
Thanks a lot for your reply but I run into a problem. When I try to run the second command it says that sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb
Selecting previously deselected package openoffice.org-debian-menus.
dpkg: regarding .../openoffice.org3.1-debian-menus_3.1-9420_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing /home/anchorschmidt/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus

---

### Post by anchorschmidt on 2009-11-20
Don't worry about it, I fixed it. Thank you so much for helping me :)

Thanks for your time.

---

