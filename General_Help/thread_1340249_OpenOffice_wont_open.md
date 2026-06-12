---
title: "OpenOffice wont open"
date: 2009-11-28
forum: General Help
---

### Post by solomon88 on 2009-11-28
I am unable to open openoffice. When I click on the desktop shortcut nothing happens. According to synaptic and Ubuntu Software Center it is installed.  I tried opening it in the terminal using [html]oowriter[/html] and this ihttp://ubuntuforums.org/showthread.php?t=1339046s what I get
[html]/usr/bin/oowriter: 2: /usr/lib/openoffice/program/soffice: not found
[/html]Does anyone know how to fix this? I had a previous issue that is still unresolved which can be found at [http://ubuntuforums.org/showthread.php?t=1339046](http://ubuntuforums.org/showthread.php?t=1339046)

Having openoffice not work s becoming a bit of an issue, as I have a lot of work to do. I downloaded AbiWord as a temporary solution but it is far from ideal. I think there is a problem with the permissions. Any ideas? Cheers.

---

### Post by Bluppie on 2009-11-28
It seems that something has been wrong with the installation.
Install ubuntu again and make an / partition of 4 gigabyte and an /Home partition off the rest off your HD. In the future you ain't loss all your data.

---

### Post by solomon88 on 2009-11-28
Thanks for the reply. Unfortunately I am a bit of a newbie and do not know how to reinstall Karmic, nor how to sort of partitions.  I am a little hesitant to try alone as that could really make a mess. How does one uninstall ubuntu? Would this fix the potential permissions issue in openoffice?

---

### Post by scouser73 on 2009-11-28
You don't need to reinstall Ubuntu again, what I suggest is that you go to your **/home** then press **Ctrl & H** [COLOR="Red"]**[which reveals the hidden folders]**[/COLOR] then look for the folder named **.openoffice.org**, right click on that folder and delete it.

Now go back to Openoffice and try to open it again, once you have clicked on it openoffice will create the same folder **.openoffice.org** but this time you shouldn't have any problems with it.

Alternatively you can follow my instructions for totally removing the Ubuntu version of openoffice and then installing a new version from the openoffice website.

Firstly, go to the OpenOffice website:[[COLOR="Red"]**Download OpenOffice.org**[/COLOR]]("http://download.openoffice.org/other.html#en-US") and download the **Linux .deb** file.

**1 -** Remove the existing version of OpenOffice if you wish with this command: > **sudo apt-get remove openoffice*.***

**2 -** Extract the .deb file, > **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** 

**3 -** You'll now see a file called **OOO310_m19_native_packed-1_en-US.9420**

**4 -** Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: > **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

**5 -** Then paste this command: > **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office menu.

---

### Post by solomon88 on 2009-11-28
Cheers Scouser, worked a treat :)

---

### Post by scouser73 on 2009-11-28
Glad to help mate, and welcome to the Ubuntu Forums.

---

