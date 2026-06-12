---
title: "Update Open Office?"
date: 2009-09-03
forum: General Help
---

### Post by kyle2595 on 2009-09-03
Hi, is there a way to update Open Office with the update manager? I there is a newer version of Open Office and I was wondering if I could get it via update manager. Thanks!

---

### Post by scouser73 on 2009-09-03
Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m19_native_packed-1_en-US.9420**

You can remove the existing version of OpenOffice if you wish with this command: [B]sudo apt-get remove openoffice*.*
[/B]
Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

---

### Post by kyle2595 on 2009-09-03
I know that, what I wanted to know if there was a way to get updates for Open Office with the Update Manager.

---

### Post by Vince N on 2009-09-03
Not without adding some kind of 3rd party respository or waiting for Ubuntu to update their own version.

---

### Post by snowpine on 2009-09-03
Ubuntu never does major updates within the six-month cycle. Jaunty will always be "frozen" at 3.0. 

The next release, Karmic Koala, comes out in October and will include 3.1.

---

### Post by scouser73 on 2009-09-03
There is a PPA being worked on, so I'd suggest that you look at the [[COLOR="Red"]**Launchpad OpenOffice PPA**[/COLOR]]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") and see when it's ready.

---

### Post by kyle2595 on 2009-09-03
I followed what [scouser73]("http://ubuntuforums.org/member.php?u=536148") said, and now when i try to open any open office document, it crashes.

---

### Post by scouser73 on 2009-09-03
I don't know why it's crashed on you, but they are the instructions I made to install previous versions of OpenOffice.

---

### Post by kyle2595 on 2009-09-03
Is there a way to uninstall what you had just told me to install?

---

### Post by scouser73 on 2009-09-03
**sudo apt-get remove openoffice*.*** will remove OpenOffice.

---

### Post by kyle2595 on 2009-09-03
Thank you for the attempt at helping me!

---

### Post by Hagar Delest on 2009-09-04
When you made heavy changes like switching from the Ubuntu version to the Sun version, better [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) also. But don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

NB: the Sun version is more stable IMHO, according to what I see on forums.

---

### Post by sports fan Matt on 2009-09-04
while removing OOO I got this error..any advice?E: openoffice.org-hyphenation-en-us: subprocess post-removal script returned error exit status 127

---

### Post by Hagar Delest on 2009-09-04
Try to remove the packages one by one in Synaptic. I remember having some troubles once, because of dependencies, a package may have to be removed after some others.

---

### Post by sports fan Matt on 2009-09-04
All fixed:)

---

### Post by kyle2595 on 2009-09-06
Is that the Open Office that comes with Karmic Koala?

---

