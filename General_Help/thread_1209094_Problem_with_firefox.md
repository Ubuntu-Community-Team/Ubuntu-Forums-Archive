---
title: "Problem with firefox"
date: 2009-07-09
forum: General Help
---

### Post by datboy on 2009-07-09
Hey im having a serious problem with firefox after i updated it.When i click on the icon to launch it i get an eror saying Could not launch 'Firefox Web Browser' Failed to execute child process "firefox" (No such file or directory) can someone help me with this please

---

### Post by philcamlin on 2009-07-09
firefox is really messed up 

just reinstall it 

sudo apt-get purge firefox

sudo apt-get install firefox 

:)

---

### Post by sdlynx on 2009-07-09
> **philcamlin said:**
> firefox is really messed up 

just reinstall it 

sudo apt-get purge firefox

sudo apt-get install firefox 

:)

+1

---

### Post by datboy on 2009-07-10
Ok will try hopefully it works

---

### Post by datboy on 2009-07-10
Ok i tried the instructions listed but it did not work

---

### Post by datboy on 2009-07-10
After i entered the commands in the terminal this is what i got
The following packages will be REMOVED:
  firefox*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 127kB disk space will be freed.
Do you want to continue [Y/n]? y   
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
(Reading database ... 212613 files and directories currently installed.)
Removing firefox ...
 
Then i went and reinstalled it  and got

The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/69.3kB of archives.
After this operation, 127kB of additional disk space will be used.
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
Selecting previously deselected package firefox.
(Reading database ... 212611 files and directories currently installed.)
Unpacking firefox (from .../firefox_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb) ...
Setting up firefox (3.0.11+build2+nobinonly-0ubuntu0.9.04.1) ...
but its not installed.....When i click on the firefox icon i get the same error Could not launch 'Firefox Web Browser' Failed to execute child process "firefox" (No such file or directory)

---

### Post by cdawley4 on 2009-07-10
datboy,

I had the same problem with mine.  I use Synaptic Package Manager and removed it, then went to Mozilla's website and downloaded Firefox.  I used the debian manager to unpack and install it.

Hope that helps.

---

