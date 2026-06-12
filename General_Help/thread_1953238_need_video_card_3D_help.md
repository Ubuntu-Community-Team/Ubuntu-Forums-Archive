---
title: "need video card 3D help"
date: 2012-04-05
forum: General Help
---

### Post by petermg on 2012-04-05
I just installed a fresh copy of Ubuntu 11.10 on a Compaq V5101US (Presario V5000 serires) laptop and I want to install the correct 3D drivers for the card.  How can I tell which card I have and what drivers I need for it?

---

### Post by petermg on 2012-04-05
Well I know it's an ATI chipset, so I'm gonna install this driver:
[http://www.ubuntuupdates.org/package/core/oneiric/restricted/updates/fglrx-updates](http://www.ubuntuupdates.org/package/core/oneiric/restricted/updates/fglrx-updates)
and hope for the best.  We'll see what happens.  I will post back.

---

### Post by 3rdalbum on 2012-04-05
[SIZE="4"]STOP NOW.[/SIZE]

[COLOR="Red"]**The fglrx driver does NOT work with the Xpress 200M. You are already using the only driver available. Installing any fglrx driver will break your system.**[/COLOR]

That's why the Additional Drivers program did not offer you a driver.

If you have installed any fglrx packages, remove them immediately.

---

### Post by petermg on 2012-04-06
> **3rdalbum said:**
> [SIZE="4"]STOP NOW.[/SIZE]

[COLOR="Red"]**The fglrx driver does NOT work with the Xpress 200M. You are already using the only driver available. Installing any fglrx driver will break your system.**[/COLOR]

That's why the Additional Drivers program did not offer you a driver.

If you have installed any fglrx packages, remove them immediately.

Uninstalled.  Thanks.  I was running into some issues with Compiz and thought that installing new drivers for my ATI IGP would help... guess I need to focus on Compiz rather.

---

### Post by mastablasta on 2012-04-06
You can upgrade drivers via Edgers PPA to see if anything was improved in development version.
 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by petermg on 2012-04-07
> **mastablasta said:**
> You can upgrade drivers via Edgers PPA to see if anything was improved in development version.
 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Ok I added that PPA, how do I upgrade the drivers?  Sorry for such a noob question.

---

