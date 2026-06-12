---
title: "Open Office 3.1 Jaunty (9.04)"
date: 2009-08-15
forum: General Help
---

### Post by SneakPeak on 2009-08-15
Hi There,

I have a bog-standard Ubuntu 9.04 system. For various reasons I wanted to upgrade to Open Office 3.1. I followed the instructions given here:

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68)

First up it did not work so I thought the problem was Ubuntu was using a non standard Java version (a guess from me because I am not very good technically)
I used Synaptic to remove everything Ubuntu Java related and then I followed the instructions in these two locations to install the latest java:

[http://www.java.com/en/download/help/5000010500.xml#100](http://www.java.com/en/download/help/5000010500.xml#100)
[http://www.64bitjungle.com/ubuntu/insta](http://www.64bitjungle.com/ubuntu/insta) ... a-runtime/

I did the recommended tests and it seems that my java is correctly installed. When I type "java -version" I get:

java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)

I then uinstalled all Open Office stuff I could find and redid the installation as per the instructions here:

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68)

But still I get the same error. Everytime I try to start any of the open office programs I get:


Please refer to the attachment


The only "error" I get during installation is during the desktop integration step when I get:

Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

The only other options I can find for installation involve using the repository:

deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main

But I have been advised against using anything other than the official Open Office files as others are not always as they should be and contain errors and hacks and corruption???

Any advice would be greatly appreciated.

Thanks

---

### Post by P4man on 2009-08-15
You're correct its best to stick with the OO version in the repo's, but if  you do need 3.1, then at least follow a recent tutorial :). here try this:

[http://webupd8.blogspot.com/2009/05/install-openoffice-31-in-ubuntu-jaunty.html](http://webupd8.blogspot.com/2009/05/install-openoffice-31-in-ubuntu-jaunty.html)

---

### Post by scouser73 on 2009-08-15
Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the Linux .deb file.

Once you have done that, extract the .deb file, **OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m11_native_packed-4_en-US.9399**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m11_native_packed-4_en-US.9399** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9393_all.deb**

Once you've done that you'll find OpenOffice 3.1.0 in Office.

---

### Post by SneakPeak on 2009-08-15
> **scouser73 said:**
> Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the Linux .deb file.

Once you have done that, extract the .deb file, **OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m11_native_packed-4_en-US.9399**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m11_native_packed-4_en-US.9399** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9393_all.deb**

Once you've done that you'll find OpenOffice 3.1.0 in Office.

Hi, 

Thanks for the reply.  I tried this but it seems to be exactly the same as the instructions given here:

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68)

The only difference is that you do the installation from a desktop folder rather than another folder.

Anyway I followed your advice and I still have exactly the same problem.

Any other advice?

Thanks

Sneaks

---

### Post by scouser73 on 2009-08-15
Sorry to hear that, I'm stuck as how you should proceed. Hopefully someone will provide a better answer for you.

---

### Post by P4man on 2009-08-15
Hate quoting myself, but this worked for me:

[http://webupd8.blogspot.com/2009/05/install-openoffice-31-in-ubuntu-jaunty.html](http://webupd8.blogspot.com/2009/05/install-openoffice-31-in-ubuntu-jaunty.html)

---

### Post by SneakPeak on 2009-08-15
This problem is solved!!!

Check out these posts on the open office forum.  The trick was to reset the user profile.

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=21657&p=98422#p98422](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=21657&p=98422#p98422)

[http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403)

[http://user.services.openoffice.org/en/forum/viewtopic.php?p=58401#p58401](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58401#p58401)

Cheers

Sneaks

---

### Post by theDaveTheRave on 2009-08-18
Hello all.

I needed the new version also ;(

so I followed scouser73's instruction

> Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the Linux .deb file.

Once you have done that, extract the .deb file, OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz then you'll see a file called OOO310_m11_native_packed-4_en-US.9399

You can remove the existing version of OpenOffice if you wish with this command: sudo apt-get remove openoffice*.*

Copy and paste OOO310_m11_native_packed-4_en-US.9399 onto the desktop then open Terminal and paste this command: sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb

Then paste this command: sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9393_all.deb

Once you've done that you'll find OpenOffice 3.1.0 in Office.


The only difference is that I downloaded into my "download" directory (as specified in the settings in Firfox). It worked a treat.

Just so as any other newb's out there understand how this works

the >  ~/Desktop/  causes the system to look into your "home" folder (for me it would be /home/davem as davem is my username)

As I say I used a different folder called downloads, the full path is /home/davem/downloads   if it had resided in another location such as maybe /documents/downloads I could have used the same syntax as scouser and just written ~/documents/downloads

however, thanks to the guys in this thread I have been able to get a nice new copy of the Open Office on my system.

so a big thanks to all of you for the info.

David

---

