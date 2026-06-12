---
title: "software center vs synaptic"
date: 2010-08-29
forum: General Help
---

### Post by SuperDuckk on 2010-08-29
Hi guys,

**-1-**

Ubuntu software center lists packages different than synaptic. Not sure but seems like some packages have duplicate entries in software center.

I search for 'disk utility' in installed software on both. Software center displays 2 additional entries;

```
Disk Utility
Manage drives and media

Startup Disk Creator
Create a startup disk using a CD or disk image
```

though the list already contains 'usb-creator-gtk' and 'gnome-disk-utility'.

**-2-**

Btw, does synaptic show only history of operations done from synaptic? When I took a look at the history, I saw a very partial list. I've used synaptic, apt-get, and software center to install / remove several packages. I was hoping to find out which packages were initially installed, and which were installed later by me.

Thank you!

---

### Post by gvernold on 2010-08-29
Ubuntu Software Centre is just a GTK+ frontend to apt. Any changes you make using apt (and therefore Software Centre) should also be reflected in Synaptic which is an alternative frontend (also based on GTK+).

The only differences I have found with Ubuntu Software Centre is that sometimes the titles of some packages are different to how they appear in Synaptic. Personally I still prefer Synaptic as a GUI interface.

I've never seen a function in Synaptic to filter software by installation date but that's not to say it doesn't exist or a custom filter can't be created for it. You could also try the File - History option which will give you a change log of your system (only native ubuntu/deb packages though).

---

### Post by SuperDuckk on 2010-08-29
Thanks for your reply gvernold!

Actually an 'installation date' property / column is what I'd like to have, but I was also talking about the history feature.

> (only native ubuntu/deb packages though)

and this may explain the history being very partial.

My software center still double lists some packages using different information. Unchecked 'universe', still the same.

---

### Post by gvernold on 2010-08-29
I've only ever seen the installation date column on an RPM package manager... not sure if there is one in the deb manager range.

The software in the repositories is all deb based in a standard installation. Synaptics won't display any packages installed from source or standard binary files.

No idea why Software Centre repeats itself. I have a desktop and a laptop based on very similar hardware and both with 32bit 10.04 but the one Software Centre seems to have about a third of the packages missing compared to the other.

Otherwise, glad to help.

---

