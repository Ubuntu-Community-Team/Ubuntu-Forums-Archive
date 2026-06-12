---
title: "Openoffice on new Ubuntu problem"
date: 2010-04-30
forum: General Help
---

### Post by maharaja2 on 2010-04-30
Hello,
i am having problem installing latest Openoffice package on my Ubuntu Netbook Remix 10.04. I did fresh install of Ubuntu Netbook Remix yesterday.

I had installed Openoffice throught the Ubuntu Software Center, but when i click on icon to start the program, it starts and then crashes.

Here is what happens in terminal:
> The application cannot be started. 
The component manager is not available.
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'


What should i do?

Thank you for your time

---

### Post by Hagar Delest on 2010-05-01
First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by jimmers on 2010-05-02
You could try this tutorial:-
  	 	 	 	 	 	  This tutorial will explain how to install latest version of openoffice in ubuntu
 You can check what is new in openoffice 3.2 from [here]("http://www.openoffice.org/dev_docs/features/3.2/")
  First go to the [OpenOffice website]("http://download.openoffice.org/other.html") and download the Linux .deb file (On your [[COLOR=#006400]_desktop_[/COLOR]]("http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html#"))
 1 - Once you have done that, extract the .deb file,
 [INDENT]OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz[/INDENT] Run the following command from terminal or just right click select extract
 [INDENT]tar xzvf OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz[/INDENT] Then you’ll see a file called OOO320_m12_native_packed-1_en-GB.9483
 2 - You can remove the existing version of OpenOffice if you wish with this command:
 [INDENT]sudo apt-get remove openoffice*.*[/INDENT] 3 - Copy and paste OOO320_m12_native_packed-1_en-GB.9483 onto the desktop then open Terminal and paste this command:
 [INDENT]sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-GB.9483/DEBS/*.deb[/INDENT] 4 - Then paste this command:
 [INDENT]sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-GB.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb[/INDENT] Once you’ve done that you’ll find OpenOffice 3.2 in Office.


Wherever your location you may have to change the en-GB part.




Good Luck

---

### Post by Hagar Delest on 2010-05-02
> **jimmers said:**
> Wherever your location you may have to change the en-GB part.
See the link I've given above, no need to bother with the full path name!

---

### Post by scouser73 on 2010-05-02
Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the **Linux .deb** file.

Once you have done that, extract the .deb file, 

OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz

Then you'll see a file called **OOO320_m12_native_packed-1_en-GB.9483**

You can remove the existing version of OpenOffice if you wish with this command: 

**> sudo apt-get remove openoffice*.***

Copy and paste OOO320_m12_native_packed-1_en-GB.9483 onto the desktop then open Terminal and paste this command: 

**> sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-GB.9483/DEBS/*.deb**

Then paste this command: 

**> sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-GB.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb**

Once you've done that you'll find OpenOffice 3.2 in Office.

---

