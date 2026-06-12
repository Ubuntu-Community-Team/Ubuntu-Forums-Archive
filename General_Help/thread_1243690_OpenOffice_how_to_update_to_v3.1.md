---
title: "OpenOffice how to update to v3.1?"
date: 2009-08-18
forum: General Help
---

### Post by UranUtan on 2009-08-18
Hi,

Using Ubuntu 9.04 x32 and x64. Update Manager run automatically everyday. And OpenOffice is still at v.3.0.1.

If I download and install the new version 3.1 from OpenOffice web site, would that conflict or break something in Ubuntu auto update system?

And BTW what is the recommended way to maintain OpenOffice up to date? And any reason why Update Manager failed to notice the new version of OpenOffice?

Thanks in advance for any help.

---

### Post by scouser73 on 2009-08-18
**Openoffice Installation 3.1.0**

Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m11_native_packed-4_en-US.9399**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m11_native_packed-4_en-US.9399** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9393_all.deb**

Once you've done that you'll find OpenOffice 3.1.0 in Office.

---

### Post by fragos on 2009-08-18
This can be done from the GUI if you first install ubuntu-tweak from [http://www.getdeb.net/download/4649/0](http://www.getdeb.net/download/4649/0). Ubuntu tweak will allow you to add the Openoffice 3.1 repository. The next time you run Update Manager you'll be offered 3.1 as an update option.

---

### Post by UranUtan on 2009-08-19
> **fragos said:**
> This can be done from the GUI if you first install ubuntu-tweak from [http://www.getdeb.net/download/4649/0](http://www.getdeb.net/download/4649/0). Ubuntu tweak will allow you to add the Openoffice 3.1 repository. The next time you run Update Manager you'll be offered 3.1 as an update option.
Works PERFECTLY (using Ubuntu Tweak 0.48 ). In the Ubuntu Tweak left menu, I selected Application -> Third Party Sources. Then I clicked Unlock and checked Open Office. There is a progression bar that update the sources. Then I forced Ubuntu to rerun Update Manager. Which now listed OpenOffice among the updates. After a few minutes and now I am with OpenOffice 3.10. Thanks very much.


> **scouser73 said:**
> **Openoffice Installation 3.1.0** Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the **Linux .deb** file. 
... etc ...

Once you've done that you'll find OpenOffice 3.1.0 in Office.

Just curious, I would like to know if I override Ubuntu by installing manually a program outside of the Update Manager, would I corrupt something? At the next Auto Update, what would happen if Ubuntu finds out that the OpenOffice suddenly is not the same than what it had installed initially?

---

### Post by scouser73 on 2009-08-19
I doubt that a program would become corrupted if you installed a program manually rather than via the Update Manager.  For instance, I installed Firefox 3.5 from a website tutorial recently and the update manager informed me of new Firefox updates for a previous version of Firefox. 

Now I was concerned that my current Firefox would somehow regress back to Firefox 3.0.XX.  What I did was to go into the **Synaptic Package Manager**, look for the Firefox 3.0.XX updates, click **Packages**, scroll to **Lock Version** and check the box, thus not getting anymore updates for that application.

---

### Post by UranUtan on 2009-08-19
Me too I installed Firefox 3.5 via an Ubuntu repository. Instructions here: [http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html)

But Firefox 3.5 is installed at a different place than FF 3.0. Therefore the two FF version exist at the same time. Now Each time I run Update Manager, I got updates for both FF 3.0 and 3.5. Your tip about "locking version" is a good idea, I am going to lock FF 3.0.

In the case of OpenOffice, the new manual install will probably overwrite the existing one (I don't know actually, just assume) I can go ahead and try it just for learning sake but I am rather busy at the moment.

---

