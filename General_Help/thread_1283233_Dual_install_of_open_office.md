---
title: "Dual install of open office?"
date: 2009-10-05
forum: General Help
---

### Post by donniep152 on 2009-10-05
I've posted and searched in the linux mint forum and thought I'd give it a shot here as well as it's a much larger community.

I installed open office from the repositories and it's broken.

Here's my post from the mint forum.  Any help would be appreciated.

Is it possible to install a second open office suite in mint gloria?
The reason I ask is that the version from the repo's is broken. If you try and repeat rows to print in calc, you get an invalid sheet reference error every time.
I've tried this fix: [http://news.softpedia.com/news/How-to-I](http://news.softpedia.com/news/How-to-I) ... 1105.shtml
and this fix: [http://user.services.openoffice.org/en/](http://user.services.openoffice.org/en/) ... ?f=74&t=68
Neither one worked.  I had the same issue

So, then I tried to install OO 2.4 from a downloaded deb and got "a later version is already installed"

All I need is to have 2.4 installed somewhere so that I can access it to do the few things that the G-OO or Ubuntu version of Open Office doesn't do right.

Lastly, why does this happen with the official versions in the repo's? When I installed 2.4 for the first time in Elyssa, vlookup didn't work right and I had to remove and reinstall from the OO website.

Many thanks,

---

### Post by Giblet5 on 2009-10-05
Take a look at VirtualBox. Install whatever you like, as many times as you like, until you run out of disk space.

I can't imagine any reason to have two installs of the same package on one system unless you're an official tester of that package - and even then, you'd use VirtualBox.

Just curious: have you filed bug reports against OO for these things that you say don't work?

---

### Post by miwaypet on 2009-10-05
In termina install "deborphan".

$sudo apt-get install deborphan

In synaptic, under settings, choose filters. Select New. Replace New Filter 1 with word "Orphan". Deselect All. Check Orphaned. Create.

Then:

$sudo apt-get remove --purge openoffice

After that use the filters tab bottom left in synaptic to select Orphan. Remove orphaned packages. 

Go to OO's website, and add repo's, gpg key, and download the latest and greatest.

---

### Post by ajgreeny on 2009-10-05
I think you can install the system by downloading the archive from Openoffice direct, making sure you get the deb archive from here and see if it overcomes the problems of the repos version.  This way used to install to /opt leaving your other install untouched, so I assume the same is still the way it works.:-
[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.1.1](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.1.1)
In this there are folders containing the actual separate .debs for the various parts of OOo.  You need to navigate to the main DEB folder with lots of debs in it using terminal and then use command ```
sudo dpkg -i *.deb
```to install all of those.  I can find no reference to obtaining the older version on their site, but I'm sure that must be available by some means, and you can install that in the same way to /opt.

EDIT:
Just found the 2.4 version here:-
[http://download.services.openoffice.org/files/stable/2.4.3/OOo_2.4.3_LinuxIntel_install_en-US_deb.tar.gz](http://download.services.openoffice.org/files/stable/2.4.3/OOo_2.4.3_LinuxIntel_install_en-US_deb.tar.gz)

To use this version you will need to make launchers to the various executables in /opt, as your current launchers and menu will not open it but take you straight to OOo v3.

---

### Post by donniep152 on 2009-10-05
Thanks.  I tried the complete remove including orphans, reinstall and I'm right back where I was using the links I had posted.
I start OO and get a document recovery loop that I can't get out of .

---

### Post by Hagar Delest on 2009-10-05
Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by donniep152 on 2009-10-06
Interesting.  I rename user to user.old  restarted OO 3.1.1 and was never asked to transfer settings.  It just created a new user...

I'm baffled!

---

