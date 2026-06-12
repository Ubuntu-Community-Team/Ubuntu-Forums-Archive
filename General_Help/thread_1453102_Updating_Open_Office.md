---
title: "Updating Open Office"
date: 2010-04-12
forum: General Help
---

### Post by OldAlgis on 2010-04-12
I use OpenOffice.org (v 3.1) extensively. I find it usable, but buggy. It came as part of ubuntu 9.10. I expect that some of the bugs have been eliminated by the Open Office developers' team.

What is the simplest way of updating OpenOffice, other than waiting for the (imminent) release of the new version of ubuntu?

Thanks in advance for all hints!

---

### Post by JDShu on 2010-04-12
This might work.

[http://www.unixmen.com/linux-tutorials/773-upgrade-to-openofficeorg-32-final-in-ubuntu-karmic-koala-via-ppa-launchpad](http://www.unixmen.com/linux-tutorials/773-upgrade-to-openofficeorg-32-final-in-ubuntu-karmic-koala-via-ppa-launchpad)

---

### Post by OldAlgis on 2010-04-13
> **JDShu said:**
> This might work.

[http://www.unixmen.com/linux-tutorials/773-upgrade-to-openofficeorg-32-final-in-ubuntu-karmic-koala-via-ppa-launchpad](http://www.unixmen.com/linux-tutorials/773-upgrade-to-openofficeorg-32-final-in-ubuntu-karmic-koala-via-ppa-launchpad)

Yes, it may work and it may not work.  It did NOT work for me...
Here is the dialog:
```


Upgrade OOo
------------
From
http://www.unixmen.com/linux-tutorials/773-upgrade-to-openofficeorg-32-final-in-ubuntu-karmic-koala-via-ppa-launchpad
Add repositories:
sudo add-apt-repository ppa:openoffice-pkgs/ppa


Update and upgrade :
 
sudo apt-get update && sudo apt-get upgrade

 you want to install it for the first time then type :
 
sudo apt-get install openoffice.org
 
Component registries might be corrupted                                                                                                                              &#9474;
 &#9474;                                                                                                                                                                      &#9474;
 &#9474; You are upgrading from a version which might have corrupted service/component registry files (*.rdb), especially /var/lib/openoffice/basis3.1/program/services.rdb   &#9474;
 &#9474; and the rdb files in /var/spool/openoffice/uno_packages/cache for installed extensions.                                                                              &#9474;
 &#9474;                                                                                                                                                                      &#9474;
 &#9474; If you experience problems with the component manager or segmentation faults involving libstore in either unopkg or OpenOffice.org, please check these files. Try    &#9474;
 &#9474; cleanly reinstalling the packages and/or using a clean user profile. 
 
```

Now when I click on the icon, a OOo v 3.1 icon flashes and disappears.

I've lost my OOo Word processor completely.  I am rather unhappy with this procedure, but thank you anyhow.

---

