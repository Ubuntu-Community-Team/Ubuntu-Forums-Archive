---
title: "Ubuntu 10.04 on Foxconn 45CSX Freezing"
date: 2010-10-04
forum: General Help
---

### Post by jgramlich on 2010-10-04
I've got a couple of these Foxconn 45CSX ITX boards with the Intel 
"Dimondville" CPU...using 1GB of Crucial DDR2.


I'm using the Ubuntu 10.04 ISO from linuxcnc.org.  It comes with EMC2 and running the installer from Ubuntu loads up the apps I need (used for CNC machine controllers).


Installs have been no problem, but after the installation of the OS...one waits about 5 minutes or so and the computer freezes.  I've done this now with 2 separate hardware setups (I'm trying to make a few of these) and had the same freezing problem with both computers.

So...I'm not looking for troubleshooting assistance...just checking to see if anyone has come across the same problem or to see if the community is aware of any known issues with this hardware/OS setup.

---

### Post by jgramlich on 2010-10-05
Update:

Turned off ACPI and ran glxgears...ran 16 hours with no crashes.

---

### Post by jgramlich on 2010-10-05
...but, this seems to cause an issue.  With ACPI off, I get just short of 700 frames every 5 seconds with glxgears...with it on I get about 1700 frames every 5 seconds...albeit the computer crashes after about 20 seconds of running glxgears.


Anyone know why I might see such a dramatic performance difference between the two?

edit:  yeah...that's probably a stupid question...nevermind on that one...

---

### Post by jgramlich on 2010-10-05
Okay...I could be completely wrong...but it seems as Foxconn has *not* fixed the BIOS/ACPI issue that has been debated ad nauseam here.

I am now attempting to use one of Foxconn's D51S mini-ITX boards.  I will update this thread with success/failure.

---

### Post by jgramlich on 2010-10-05
The Foxconn D51S has been running glxgears with no problems with ACPI enabled since my last post.  I'm going to go with "that other model mobo does not work with ubuntu 10.04".

---

