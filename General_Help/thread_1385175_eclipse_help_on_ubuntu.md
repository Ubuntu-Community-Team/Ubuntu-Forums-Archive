---
title: "eclipse help on ubuntu"
date: 2010-01-19
forum: General Help
---

### Post by gsandorx on 2010-01-19
Hi, 
I have installed Eclipse on my Ubuntu laptop, and I'm trying to use the PyDev plugin. I tried to installed it using the Eclipse's software manager, but I'm getting errors with all the mirrors I found for PyDev. 
I downloaded PyDev .zip, but I want to know where am I supposed to unzip it to install it. On Windows, I just needed to unzip the plugin in the "dropins" folder and voila!
Any help?
Cheers, 
Sandor

---

### Post by kellemes on 2010-01-19
The official mirror gives errors?
What kind of errors?

* [http://pydev.org/updates](http://pydev.org/updates)

nightly builds:
* [http://pydev.org/nightly](http://pydev.org/nightly)

---

### Post by gsandorx on 2010-01-19
This is the error I get from [http://pydev.org/updates](http://pydev.org/updates). I also tried the nightly builds and a mirror from ....mmhh.. I can't remember right now, but the URL starts with something like "fabio"

"
An error occurred while installing the items
  session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.provisional.p2.engine.phases.Install, operand=null --> [R]org.eclipse.ant.ui 3.4.1.v20090901_r351, action=org.eclipse.equinox.internal.p2.touchpoint.eclipse.actions.InstallBundleAction).
  The artifact file for osgi.bundle,org.eclipse.ant.ui,3.4.1.v20090901_r351 was not found.

"

Can't I use the zip??  :)

Cheers, 
Sandor

---

### Post by kellemes on 2010-01-19
> **gsandorx said:**
> 

Can't I use the zip??  :)

Cheers, 
Sandor

Don't know.. :(

Have installed Eclipse/Pydev ones, the only thing I remember is that the installation of Pydev went fine and for some reason I chose another Python-IDE ;-)

---

### Post by Rob_H on 2010-01-19
I have PyDev running in Eclipse under Karmic. I installed it from the main update site ([http://pydev.org/updates](http://pydev.org/updates)) a few weeks ago.

Did you install Eclipse from the repo or manually? I did it manually at first and I had trouble getting some plugins to coexist peacefully (e.g. CDT and PyDev). I'd install CDT and PyDev would disappear. Very strange. But then I installed Eclipse from the repo and everything works fine.

---

### Post by Beaon on 2010-03-18
Still have this problem with this. I installed my Eclipse from the Software Centre list, ver 3.5.1. When I try to install the Python software on top of it, from:

[http://pydev.org/updates](http://pydev.org/updates)

I get
An error occurred while installing the item

  session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.provisional.p2.engine.phases.Install, operand=null --> [R]org.eclipse.ant.ui 3.4.1.v20090901_r351, action=org.eclipse.equinox.internal.p2.touchpoint.eclipse.actions.InstallBundleAction).

  The artifact file for osgi.bundle,org.eclipse.ant.ui,3.4.1.v20090901_r351 was not found.

Any thoughts?

---

