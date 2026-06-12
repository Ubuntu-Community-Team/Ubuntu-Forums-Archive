---
title: "Questions from a New User"
date: 2010-08-09
forum: General Help
---

### Post by roadizzle on 2010-08-09
My experience with linux comes from a 3 month tech school class 8 years ago (used Red Hat 7.2)

Ubuntu sounds like a great switch from XP.

Here's my situation.

I've installed 10.04 using wubi to test compatibility with my laptop hardware and such. I have a couple issues that I'm hoping somebody here has seen and have quick fixes for.

Openoffice(3.2) will not load properly, it pulls up the splash screen then disappears once the loading bar fills, and nothing opens. If i try to open a specific file I get a generic error message after splash screen and it closes.

My other question is: How much performance is sacrificed with using wubi to install to a virtual drive. My system feels very laggy when loading or switching applications. System Specs: 1.8GHz AMD Turion w/1GB DDR ram.

---

### Post by bergfly on 2010-08-09
On the second issue, are you trying to install wubi inside a virtual machine on a windows box. The spec of your machine is going to be borderline for running Linux inside of windows, although it will run great on that machine by itself. Not sure if I understand the issue correctly!



On the first issue, you will need to find out where Open office is failing as this seems a little strange. The best way to do this is to run open office from inside a terminal window. 

Open terminal like this

[IMG]http://beginlinux.com/images/ubuntu/html5_1.gif[/IMG]

and then type openoffice.org in the black window. Copy and paste the code from the terminal window here and we can look at it

thanks

---

### Post by roadizzle on 2010-08-09
Open office Error from terminal: terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'


I'm not sure on the terminology for wubi. I ran wubi and installed Ubuntu as a second boot option. In windows it just appears as a folder. Not sure if "virtual drive" is the lingo I'm looking for here. Would installing Ubuntu this way as opposed to a pure install cause my performance issues?

---

### Post by Hagar Delest on 2010-08-10
For OOo, you can first try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try to install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

The only thing you need to know about OOo under Ubuntu is that the version installed by default is the Novell build (go-oo). More features but also more bugs. That's why I only use the official build from the OOo web site.

---

### Post by roadizzle on 2010-09-06
Well it looks like the performance issues were due to failing memory. That much has been fixed. Still no solution to the OOffice issues.

---

### Post by scouser73 on 2010-09-06
> **roadizzle said:**
> Well it looks like the performance issues were due to failing memory. That much has been fixed. Still no solution to the OOffice issues.

As suggested by Hagar de l'Est, I would recommend removing the version of OpenOffice that came with Ubuntu and downloading & installing from the OpenOffice website.

Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the Linux .deb file to your desktop

Once you have done that, extract the .deb file, 

OOo_3.2.1_LinuxIntel_install_en-GB_deb.tar.gz

Then you'll see a file called OOO320_m18_native_packed-1_en-GB.9502

Remove the existing version of OpenOffice with this command: 

sudo apt-get remove openoffice*.*

Then paste this command:

sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-GB.9502/DEBS/*.deb

Then paste this command: 

sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-GB.9502/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9502_all.deb

Once you've done that you'll find OpenOffice 3.2.1 in Office.

---

### Post by roadizzle on 2010-09-06
Thanks! It's up and running!

---

