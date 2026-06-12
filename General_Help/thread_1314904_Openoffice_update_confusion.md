---
title: "Openoffice update confusion"
date: 2009-11-04
forum: General Help
---

### Post by Stolea on 2009-11-04
My Openoffice says version 3.0 at the startup and the About info says ver. 3.0.1.
When I check in Synaptic it says that this is the latest version available.
However, my other Ubuntu computer has been updated to 3.1. Why does one computer update and the the other doesn't? They are identical machines, so theoretically they should do the same updates.

I downloaded version 3.1.1. from Sun, but when I try to run the deb files in the package I get the following error message:
> Error: Dependency is not satisfiable: openoffice.org-ure

Any ideas what is happening anyone?
Cheers

---

### Post by Stolea on 2009-11-05
bump. any takers?

---

### Post by kixome on 2009-11-05
yes, go back to 8.04

---

### Post by Stolea on 2009-11-05
anything more helpful?

---

### Post by scouser73 on 2009-11-05
Firstly, go to the OpenOffice website: [[COLOR="Red"]**OpenOffice.org**[/COLOR]]("http://download.openoffice.org/other.html") and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m19_native_packed-1_en-US.9420**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

---

### Post by touf on 2009-11-05
Hi, I tried to do like tou suggested, removed OO-3.0 and installed the deb for OO-3.1.1...everything seemed right, but when I start OO swith to the "OpenOffice document recovery"....and loop between the differents windows of the recovery tool. It's not possible to open any document.
I'm on Ubuntu 9.04.
Thanks for help/suggestions
Touf

---

### Post by touf on 2009-11-05
In synaptic I found out that there were some packages (language & translations) from ubuntu 8.10. I removed it and eveything is OK now...

---

### Post by Stolea on 2009-11-05
I had exactly the same file recovery problem.
The trick is to understand that the Ubuntu version and the general release versions are incompatible. As a result you must un-install **ALL** the openoffice files, especially any of the ones with "ubuntu" in the version listing.
It took me two goes to get it right, but it definitely is worth the transistion effort.

Here is a how to link from one of the OpenOffice team

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68")

---

