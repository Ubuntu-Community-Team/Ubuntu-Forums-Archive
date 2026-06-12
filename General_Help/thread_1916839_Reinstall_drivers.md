---
title: "Reinstall drivers?"
date: 2012-01-28
forum: General Help
---

### Post by Stonecold1995 on 2012-01-28
Hi everyone (I'm new here).  Okay, so I've been having problems with Kubuntu.  I had to do a hard-reboot while some of the software was updating, and apparently that caused some of the drivers to become corrupt.  For example, the touchpad (it's an HP laptop with a touchpad, by the way) isn't responsive and it says "no touchpad detected", videos will play but without sound, the screen brightness won't change, and no network is detected (even though I have a perfectly good router).  So re-installing every driver (or updating them) would fix the problem, right? Is there a way to automatically re-install every driver without loosing any data (preferably through Terminal)?  Like some command that recovers or fixes them?

Thanks.

---

### Post by Rodney9 on 2012-01-28
This page will help you - 

[http://galigio.org/2009/11/29/how-to-repair-a-bad-upgrade-on-ubuntu/](http://galigio.org/2009/11/29/how-to-repair-a-bad-upgrade-on-ubuntu/)

and

[https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowTo](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowTo)

or

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)


Rodney

---

### Post by Stonecold1995 on 2012-01-28
> **Rodney9 said:**
> This page will help you - 

[http://galigio.org/2009/11/29/how-to-repair-a-bad-upgrade-on-ubuntu/](http://galigio.org/2009/11/29/how-to-repair-a-bad-upgrade-on-ubuntu/)

and

[https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowTo](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowTo)

or

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)


Rodney

Uh, I don't have internet because the driver isn't working...  Will using "sudo apt-get update" work even without internet?  Or is there a way to download the packages using Windows and then install them on Kubuntu (they're both on the same partition).

---

### Post by raja.genupula on 2012-01-28
> **Stonecold1995 said:**
> Uh, I don't have internet because the driver isn't working...  Will using "sudo apt-get update" work even without internet?  Or is there a way to download the packages using Windows and then install them on Kubuntu (they're both on the same partition).

Yeah we can download the divers from windows and you can install them . with out internet connection updating not possible . so download them from Windows and install them in ubuntu .


[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

use that link
All the best .

---

### Post by Stonecold1995 on 2012-01-29
Wait, do I have to download and manually install all of those?  I see hundreds of packages...  Is there a way to download a single package that re-installs or recovers every necessary driver?  Or better yet, some program that fixes corrupt drivers but that doesn't need the internet?

Also, if I can just fix the internet driver, then could I have the system perform an automatic update?  Would an update fix the corrupt drivers?

---

### Post by Rodney9 on 2012-01-29
You could back-up all your data (docs, photos etc) and install again.

Rodney

---

