---
title: "wine(program)/update manger/software center problem"
date: 2012-08-21
forum: General Help
---

### Post by yellowwinner on 2012-08-21
hello
recently Ubuntu 12.04 64-bit update manger has stopped working.
it says package system is broken. at the same time Ubuntu software center needs catalog update to install or remove programs, so I cant just uninstall wine.
Code below and photo in attachments.(cropped as best i could)

please help,yellowwinner



```
The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.1.2ubuntu7 is installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu10 is installed
         Depends: wine1.4-amd64 (= 1.4-0ubuntu4.1) but 1.4-0ubuntu4.1 is installed
         Depends: wine1.4-i386 (= 1.4-0ubuntu4.1) but it is a virtual package
wine1.4-i386:i386: PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.16.1.2ubuntu7 is installed
                   Depends: libc6 (>= 2.9) but 2.15-0ubuntu10 is installed
                   Depends: libglib2.0-0 (>= 2.16.0) but 2.32.3-0ubuntu1 is installed
                   Depends: libgphoto2-2 (>= 2.4.10.1) but 2.4.13-1ubuntu1.2 is installed
                   Depends: libgphoto2-port0 (>= 2.4.10.1) but 2.4.13-1ubuntu1.2 is installed
                   Depends: liblcms1 (>= 1.15-1) but 1.19.dfsg-1ubuntu3 is installed
                   Depends: libldap-2.4-2 (>= 2.4.7) but 2.4.28-1.1ubuntu4.1 is installed
                   Depends: libmpg123-0 (>= 1.6.2) but 1.12.1-3.2ubuntu1 is installed
                   Depends: libopenal1 (>= 1:1.13) but 1:1.13-4ubuntu3 is installed
                   Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-5.1ubuntu4.1 is installed
                   Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
                   Depends: wine1.4-common (= 1.4-0ubuntu4) but 1.4-0ubuntu4.1 is installed

```

---

### Post by slixz85 on 2012-08-21
> **yellowwinner said:**
> hello
recently Ubuntu 12.04 64-bit update manger has stopped working.
it says package system is broken. at the same time Ubuntu software center needs catalog update to install or remove programs, so I cant just uninstall wine.
Code below and photo in attachments.(cropped as best i could)

please help,yellowwinner



```
The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.1.2ubuntu7 is installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu10 is installed
         Depends: wine1.4-amd64 (= 1.4-0ubuntu4.1) but 1.4-0ubuntu4.1 is installed
         Depends: wine1.4-i386 (= 1.4-0ubuntu4.1) but it is a virtual package
wine1.4-i386:i386: PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.16.1.2ubuntu7 is installed
                   Depends: libc6 (>= 2.9) but 2.15-0ubuntu10 is installed
                   Depends: libglib2.0-0 (>= 2.16.0) but 2.32.3-0ubuntu1 is installed
                   Depends: libgphoto2-2 (>= 2.4.10.1) but 2.4.13-1ubuntu1.2 is installed
                   Depends: libgphoto2-port0 (>= 2.4.10.1) but 2.4.13-1ubuntu1.2 is installed
                   Depends: liblcms1 (>= 1.15-1) but 1.19.dfsg-1ubuntu3 is installed
                   Depends: libldap-2.4-2 (>= 2.4.7) but 2.4.28-1.1ubuntu4.1 is installed
                   Depends: libmpg123-0 (>= 1.6.2) but 1.12.1-3.2ubuntu1 is installed
                   Depends: libopenal1 (>= 1:1.13) but 1:1.13-4ubuntu3 is installed
                   Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-5.1ubuntu4.1 is installed
                   Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
                   Depends: wine1.4-common (= 1.4-0ubuntu4) but 1.4-0ubuntu4.1 is installed

```

i have run into a similar problem before using ubuntu 32 bit. i believe this could of helped it but honestly don't know for sure if this will work but it shouldn't hurt.

sudo dpkg --configure -a (helps fix package system)
sudo apt-get update
sudo apt-get -f install (fixes installation) *(make sure it is not trying to uninstall main programs like a lot of them)
sudo apt-get dist-upgrade
sudo apt-get autoremove (when you do this if you kinda know what to look for make sure it is not trying to uninstall alot of main programs, if so let me know some more)
sudo apt-get autoclean
and run sudo dpkg --configure -a again (i run this alot it helps out also with a lock permission error every once in awhile.

---

### Post by slixz85 on 2012-08-21
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto) this is a great howto made by ubuntu

---

### Post by yellowwinner on 2012-08-21
> **slixz85 said:**
> i have run into a similar problem before using ubuntu 32 bit. i believe this could of helped it but honestly don't know for sure if this will work but it shouldn't hurt.

sudo dpkg --configure -a (helps fix package system)
sudo apt-get update
sudo apt-get -f install (fixes installation) *(make sure it is not trying to uninstall main programs like a lot of them)
sudo apt-get dist-upgrade
sudo apt-get autoremove (when you do this if you kinda know what to look for make sure it is not trying to uninstall alot of main programs, if so let me know some more)
sudo apt-get autoclean
and run sudo dpkg --configure -a again (i run this alot it helps out also with a lock permission error every once in awhile.

thanks,from sudo apt-get autoremove back it gave me error but sudo apt-get autoclean worked fine. also 64-bit and 32-bit is no different other than graphics,I think. but stil,thank you

---

### Post by slixz85 on 2012-08-21
> **yellowwinner said:**
> thanks,from sudo apt-get autoremove back it gave me error but sudo apt-get autoclean worked fine. also 64-bit and 32-bit is no different other than graphics,I think. but stil,thank you

yeah your welcome i knew that about 32 64 but just posted that as a hint in case you didn't. so your good now right? what error

---

### Post by jradmwright on 2012-09-07
sudo apt-get build-dep wine

fixed same error for me

---

### Post by GMeister on 2012-10-07
Bump!

Same issue (ish).

Some history:  Due to foolish partition config, I ran out of usable space on my / mount and so had to do some partition-manoeuvring to free up the space - new packages were being installed when I originally ran out space, which caused updates to fail.  When reconfiguring the partitions, I also took the opportunity to roll back to 12.04 from 12.10 by reinstalling... I suspect all this combined is what has caused the package problems.

I've tried apt-get management, but it doesn't work.  I've also attempted to use synaptics, to no avail.

Any ideas?

---

### Post by crua9 on 2013-01-20
> **GMeister said:**
> Bump!

Same issue (ish).

Some history:  Due to foolish partition config, I ran out of usable space on my / mount and so had to do some partition-manoeuvring to free up the space - new packages were being installed when I originally ran out space, which caused updates to fail.  When reconfiguring the partitions, I also took the opportunity to roll back to 12.04 from 12.10 by reinstalling... I suspect all this combined is what has caused the package problems.

I've tried apt-get management, but it doesn't work.  I've also attempted to use synaptics, to no avail.

Any ideas?

I actually had the same problem as the guy above me.  I didn't partition my computer, but I did have Ubuntu installed on here before. But, when I installed Ubuntu 12.10, the Windows installer uninstalled whatever Ubuntu I had before. 
Anyways, I ran into this problem, and I ran into a few of these forums. [http://askubuntu.com/questions/101822/package-dependencies-cannot-be-resolved-error-when-installing-software](http://askubuntu.com/questions/101822/package-dependencies-cannot-be-resolved-error-when-installing-software) 
Anyways, I did what they said and that did nothing, and at some cases it made things worst. So I figured it was 12.10, so I downgraded to the LTS 12.04. 
Same problem :(. 

Then I ran into this forum, and I followed the instructions that was given.  Anyways, Wine is now installing, but very very very slowly.  But, it worked. 
I'm going to update to 12.10. I will tell you here if that doesn't work.

---

