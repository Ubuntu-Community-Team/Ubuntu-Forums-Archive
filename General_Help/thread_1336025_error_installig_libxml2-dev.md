---
title: "error installig libxml2-dev"
date: 2009-11-24
forum: General Help
---

### Post by alin19 on 2009-11-24
i don't know why i'm getting this error and how to fix it
:(

root@alin-laptop:~# apt-get install libxml2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxml2-dev: Depends: libxml2 (= 2.6.32.dfsg-5ubuntu4.2) but 2.7.5.dfsg-1ubuntu1 is to be installed
E: Broken packages



root@alin-laptop:~/Desktop/arhive/php-5.3.1# apt-cache show libxml2|grep Version
Version: 2.7.5.dfsg-1ubuntu1
Version: 2.6.32.dfsg-5ubuntu4.2
Version: 2.6.32.dfsg-5ubuntu4

---

### Post by mc4man on 2009-11-24
late here and have to go but you should be able to figure this out

> Version: 2.7.5.dfsg-1ubuntu1  < - current karmic 
Version: 2.6.32.dfsg-5ubuntu4.2  < - jaunty updates
Version: 2.6.32.dfsg-5ubuntu4  <- jaunty

> libxml2-dev: Depends: libxml2 (= 2.6.32.dfsg-5ubuntu4.2) 
Your package list is showing the jaunty update version as the avail. package.

If you're running karmic then ck. your sources for jaunty repo's, maybe also clean your apt cache, remove the old versions, ect.
apt-get clean
apt-get autoremove
apt-get update

If you're running jaunty then why do you have the karmic version installed...?, ect.

---

### Post by alin19 on 2009-11-24
i'm new with ubuntu, i don't know what i'm using, i think is jaunty, 
how do i install karmic

thanks for your help

L.e: i have ubuntu 9.10 
L.L.e: it is karmic, i have figure this out

---

### Post by alin19 on 2009-11-24
it is all gone,

i give : 
apt-get autoremove libxml2 ; and deleted a lot of program and now i can't even enter the x window, just terminal  it is show, :(


now i have to format my computer again

---

