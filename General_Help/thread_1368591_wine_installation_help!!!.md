---
title: "wine installation help!!!"
date: 2009-12-30
forum: General Help
---

### Post by inversionce on 2009-12-30
i need help installing wine to play starcraft. im using ubuntu and when i try to install from the terminal i get this message:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
wine: Depends: libasound2 (> 1.0.14) but 1.0.13-1ubuntu5 is to be installed
Depends: libgphoto2-2 (>= 2.4.0) but 2.3.0-0ubuntu4 is to be installed
Depends: libgphoto2-port0 (>= 2.4.0) but 2.3.0-0ubuntu4 is to be installed
Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed
PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.13.24ubuntu6 is to be installed
E: Broken packages

---

### Post by teward on 2009-12-30
provide Distro info please.

Had no issues installing Wine in 9.04, and I had to because I had to wipe the drive.

---

### Post by USB_NL on 2009-12-30
get term windw

```
sudo apt-get install wine
```

---

### Post by inversionce on 2009-12-30
where do i find distro info?

and i put in sudo apt-get install wine  and got the same results

---

### Post by ron999 on 2009-12-30
> **inversionce said:**
> where do i find distro info?



System > Administration > System Monitor

That opens System Monitor, click on the 'System' tab.

---

### Post by inversionce on 2009-12-30
**Ubuntu**
  Release 7.04 (fiesty)

**hardware**
  Memory: 496.0 MB
  Processor: intel(r) Pentium(R) 4 CPU 1.80GHz

**System status **
  Available disk space: 30.7

---

### Post by ron999 on 2009-12-30
Hi
Because you're running Fiesty, you'll need to install an old version of Wine.
Download the deb and install it using either 'right-click install with GDebi'.
Or use GDebi Package Installer from the menu.
Get the appropriate old Wine deb from here:-
[http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html")

---

### Post by inversionce on 2009-12-30
ok i choose  Wine 0.9.35 i386, -dev

---

### Post by ron999 on 2009-12-30
Ok

---

### Post by inversionce on 2009-12-30
ok i saved it, and the package installer popped up and installed it. now what do i do?

---

### Post by ron999 on 2009-12-30
> **inversionce said:**
> ok i saved it, and the package installer popped up and installed it. now what do i do?
Well, if it's installed there should be a Wine section added to your main menu under 'Applications'. If it's not there you might need to reboot.

---

### Post by inversionce on 2009-12-30
it wasnt there so I restarted and its still not there

---

### Post by ron999 on 2009-12-30
> **inversionce said:**
> it wasnt there so I restarted and its still not there
OK, I'm not sure about that.
If you have the installation file for that starcraft game it will be a file that ends in **.exe**
Try right-clicking on it and see if it gives you the option to 'Open with Wine'

---

### Post by inversionce on 2009-12-30
its not there...i tryed different dev packages too

---

### Post by USB_NL on 2009-12-30
> **inversionce said:**
> its not there...i tryed different dev packages too
have you tried searching in synaptic package manager

---

### Post by USB_NL on 2009-12-30
Try using a M$windows install with wine!

---

### Post by inversionce on 2009-12-30
its there with a green box and a star and when i click to upgrade this comes up:

wine:
  Depends: libasound2 (>1.0.14) but 1.0.13-1ubuntu5 is to be installed
  Depends: libgphoto2-2 (>=2.4.0) but 2.3.0-0ubuntu4 is to be installed
  Depends: libgphoto2-port0 (>=2.4.0) but 2.3.0-0ubuntu4 is to be installed
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
  Depends: zlib1g (>=1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.13.24ubuntu6 is to be installed

---

### Post by USB_NL on 2009-12-30
Aply dependencies ;)

---

### Post by USB_NL on 2009-12-30
> **USB_NL said:**
> Try using a M$windows install with wine!
copy the folder

---

### Post by inversionce on 2009-12-30
copy what folder? lol. im just really confused on what to do now

---

### Post by ron999 on 2009-12-31
> **inversionce said:**
>  what to do now
Hi
There's a separate forum category for Wine, maybe you can get some more specialized advice from there.
This is the link:-[http://ubuntuforums.org/forumdisplay.php?f=313]([URL="http://ubuntuforums.org/forumdisplay.php?f=313")

Good luck
:)

---

### Post by MelDJ on 2009-12-31
have you gone to synaptic and fixed the broken packages?

---

### Post by USB_NL on 2009-12-31
> **inversionce said:**
> copy what folder? lol. im just really confused on what to do now

Wine with MSwindows games sometimes can be played from the windows installation folder and not be installed with Wine Do you have the game on MS Windows? on your PC? than you can use or copy that folder and run the exe file

install with windows and run with linux thrue wine I mean

---

