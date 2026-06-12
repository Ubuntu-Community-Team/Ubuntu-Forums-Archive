---
title: "Updating Problems"
date: 2009-06-27
forum: General Help
---

### Post by gspira on 2009-06-27
I'm having all sorts of problems updating the Ubuntu 9.04

First I get a "Not all updates can be installed" pop-up

The pop-up tells me to run a partial upgrade, so I do

The upgrade starts, but while reading the cache, up pops up a new message:


Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.


I've been getting this for 2 weeks, so it's not transient

Alos, when I try to update my programs via the synaptic package manger, I run into these errors:

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/ure_1.5.0+OOo3.1.0-1ubuntu1~jaunty1_i386.deb](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/ure_1.5.0+OOo3.1.0-1ubuntu1~jaunty1_i386.deb)
  404 Not Found


I recall installing an openoffice once before Ubuntu was ready with it, so maybe taht's causing my problems.  But I have no real idea what to do about; I don't yet have much ubuntu expertise.



Thnaks for any help.

Greg

---

### Post by pastalavista on 2009-06-27
Open System > Administration > Software Sources and click the 'Third party' tab. Uncheck the launchpad/openoffice listing (you could delete it probably) and then run apt-get update again.

---

### Post by gspira on 2009-06-27
> **pastalavista said:**
> Open System > Administration > Software Sources and click the 'Third party' tab. Uncheck the launchpad/openoffice listing (you could delete it probably) and then run apt-get update again.

That worked, though it required a bit of detective work.  I didn't have a launchpad/openoffice entry.  However, I did have serveral "disabled on update to jaunty" entries and when I tried to edit them, I found one had a uri of launchpad/openoffice, so I unchecked that, and all was well




Thanks,
Greg

---

### Post by pastalavista on 2009-06-27
> **gspira said:**
> That worked, though it required a bit of detective work.  I didn't have a launchpad/openoffice entry.  However, I did have serveral "disabled on update to jaunty" entries and when I tried to edit them, I found one had a uri of launchpad/openoffice, so I unchecked that, and all was well

Thanks,
Greg

You're welcome. I had few apps disabled when I first upgraded too. The Upgrade really was pretty buggy at first but a few updates and reconfigurations, everything's perfect now except my graphics card 3D effects and I don't need them that much or I'd have to go back to Intrepid. I only miss google-earth.

---

