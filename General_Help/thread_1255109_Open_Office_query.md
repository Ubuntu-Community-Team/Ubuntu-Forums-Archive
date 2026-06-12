---
title: "Open Office query"
date: 2009-09-01
forum: General Help
---

### Post by Gary128 on 2009-09-01
First post by new user.  What is the latest version of open office supported by 9.04?  I have 3.1 installed in Win Vista.  When I installed 9.04 from CD, version installed was 3.0.  I upgraded by requesting productivity suite in add/remove, I still have 3.0.  Is this how it should be?

Hope this is not a dumb question!

---

### Post by P4man on 2009-09-01
The repositories (where you install software from using add/remove software or synaptic) do not always have the latest available version. They do however, have a version that is tested and supported with your ubuntu version. 

 If you really need the latest version, you can add a another repository at your own risk, and install from there. Here is a how to :

[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

---

### Post by Gary128 on 2009-09-01
Thank you.  I will watch for future updates.

---

### Post by P4man on 2009-09-01
Dont hold your breath :)
Its entirely possible they wont put oo 3.1 in the official repo's until the Karmic (ubuntu 9.10) comes out next month, and even then they may not put it in the jaunty repo's.

If you really miss something in oo 3.0.1, follow the above approach. If you don't miss anything (like me ;) ) then be happy with OO 3.0.1 :p

---

### Post by Hagar Delest on 2009-09-03
Or try the Sun version, it has always worked fine for me: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by scouser73 on 2009-09-03
To install the latesr version of OpenOffice, firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m19_native_packed-1_en-US.9420**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

---

