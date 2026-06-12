---
title: "ClamTK won't update"
date: 2010-09-03
forum: General Help
---

### Post by deviator on 2010-09-03
hi, i've tried everything including gksu clamtk

but when i go to help > check for updates

it says my virus definitions are up to date and there is a new version of clamtk available but no way to download it.

i also installed it via synaptic package manager and not repositories.

halp :o

---

### Post by inameiname on 2010-09-03
The version of Clamtk in Synaptic (aka, the official repos) sadly won't update. But you can download the latest version as a deb file and install by going here:

[http://sourceforge.net/projects/clamtk/files/](http://sourceforge.net/projects/clamtk/files/)

Only the deb file is necessary.

---

### Post by deviator on 2010-09-03
thankyou:D

---

### Post by inameiname on 2010-09-03
Sure. Yeah, it's sad that clamav seems to update, but not clamtk. Not sure why that is. Although, my antivirus engine has been outdated for a month now, and the latest release of it still hasn't been added to the repos, so not sure what's up with that.

---

### Post by DAB4970 on 2010-11-15
is there a different way to update the antivirus engine?  (assuming that there is one available)

---

### Post by dcstar on 2010-11-16
> **DAB4970 said:**
> is there a different way to update the antivirus engine?  (assuming that there is one available)

Add the Backports to your software, or go here and get the .deb packages:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by LakesideLoafer on 2010-11-16
Try this - it worked for me. Start ClamTK, go to Advanced and then Rerun AV Setup Wizard and click on Single User and then save. It should then allow you to update virus signatures from the GUI.

---

### Post by inameiname on 2010-11-18
This ppa will have the latest version of the engine:

deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) maverick main

Sadly, clamtk isn't as up-to-date, so that's why you have to download it from the website.

---

### Post by DAB4970 on 2010-11-28
I added this 

deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) maverick main

to the sources list and was able to get updated av engine.  All is well.
Thanks to all in this post and other posts.

---

### Post by DAB4970 on 2010-12-02
And now that ClamTK says there's another updated AV engine, I went to the software sources list, selected the ppa for clamav and edited the distribution field to say "Natty" instead of "Maverick" and now ClamTK is again updated.

---

### Post by inameiname on 2010-12-03
I noticed that too, but rarely do I just upgrade a package using a newer Ubuntu version for fear of it not working as well on a computer. I think I'm just going to wait until it is updated in Lucid in one of my PPAs.

---

### Post by labinnsw on 2010-12-03
My Lucid clamav engine is: deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main and it is up to date.

---

### Post by inameiname on 2010-12-04
Ah, yeah, the Lucid repo just updated itself to the latest version within the past day, as noticed by labinnsw, so there isn't a need to update with the Natty version.

And checking on mine, using Maverick, it's also updated to 0.96.5 too.

---

