---
title: "how to reinstall previous version of sun-java6-jre"
date: 2011-03-09
forum: General Help
---

### Post by rdh61 on 2011-03-09
I am having the same trouble as described in thread 

[http://ubuntuforums.org/showthread.php?t=1642858](http://ubuntuforums.org/showthread.php?t=1642858)

OpenOffice base search runs unusably slowly after upgrading from sun-java6-jre-1.6.0.22 to sun-java6-jre-1.6.0.24. 

How can I reinstall the previous version? When I  try:

sudo apt-get install sun-java6-jre-1.6.0.22

I am told:

Couldn't find package sun-java6-jre-1.6.0.22

Thanks for your help.

---

### Post by zenwalker on 2011-03-09
Get it manually or search for correct package name from here packages.ubuntu.com

---

### Post by gandaran on 2011-03-09
> **rdh61 said:**
> I am having the same trouble as described in thread 

[http://ubuntuforums.org/showthread.php?t=1642858](http://ubuntuforums.org/showthread.php?t=1642858)

OpenOffice base search runs unusably slowly after upgrading from sun-java6-jre-1.6.0.22 to sun-java6-jre-1.6.0.24. 

How can I reinstall the previous version? When I  try:

sudo apt-get install sun-java6-jre-1.6.0.22

I am told:

Couldn't find package sun-java6-jre-1.6.0.22

Thanks for your help.
no, it's not possible because they remove the old version from the canonical partner repository when they update the java package.
but maybe you can still get the update_22 version from the sun-java PPA, try adding the [PPA repo]("https://launchpad.net/~sun-java-community-team/+archive/sun-java6") then update software package list and check in synaptic if that version is still there.

---

### Post by rdh61 on 2011-03-10
Thanks Gandaran, I think you led me onto the right track. A full description of the solution is here:

[http://www.mail-archive.com/users@libreoffice.org/msg02994.html](http://www.mail-archive.com/users@libreoffice.org/msg02994.html)

But note: "Maverick Main" should be "maverick main" (lower case).

---

