---
title: "Stop being notified for unwanted updates"
date: 2011-11-27
forum: General Help
---

### Post by theodorekon on 2011-11-27
Hi,
I would like to exclude some of the updates shown in my update manager. There is for example a facebook plugin update that I do not care for since I do not use facebook. I do not want to remove any of my repositories, I just want to stop being notified for specific updates. In windows update this is done by right clicking on the unwanted update and selecting hide update. Is there something similar in ubuntu??

Thanks in advance


PS I use Ubuntu 11.10 64bit by the way.

---

### Post by drs305 on 2011-11-27
I was trying to find a way to lock the version of a package via Software Center since Synaptic seems out of fashion these days.  I was unable to find a way to do it.

The GUI method in previous versions has been to 'lock' the package via Synaptic. You may have to install Synaptic, but once you do, you can lock any package to the current version and I *think* that will stop the reminders. Try it, and if it still keeps reminding you, please report back.

Here is a link:

[http://ubuntuguide.net/lock-package-versionskeep-application-at-specific-version-in-ubuntu]("http://ubuntuguide.net/lock-package-versionskeep-application-at-specific-version-in-ubuntu")

---

### Post by pretty_whistle on 2011-11-27
> **drs305 said:**
> I was trying to find a way to lock the version of a package via Software Center since Synaptic seems out of fashion these days.  I was unable to find a way to do it.

The GUI method in previous versions has been to 'lock' the package via Synaptic. You may have to install Synaptic, but once you do, you can lock any package to the current version and I *think* that will stop the reminders. Try it, and if it still keeps reminding you, please report back.

Here is a link:

[http://ubuntuguide.net/lock-package-versionskeep-application-at-specific-version-in-ubuntu]("http://ubuntuguide.net/lock-package-versionskeep-application-at-specific-version-in-ubuntu")
It worked!  I had the same issue too but not anymore!

Thanx!

---

### Post by drs305 on 2011-11-27
I'll add that 'locking' the version in Synaptic doesn't stop APT from trying to update packages via the command line (apt-get upgrade). For some reason, the GUI lock and terminal lock have always been separated.

To lock a package from apt-get upgrades, you have to 'hold' a package. Here is a link to the Community documentation that explains it. 
[https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages]("https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages")

---

### Post by pretty_whistle on 2011-11-27
> **drs305 said:**
> I'll add that 'locking' the version in Synaptic doesn't stop APT from trying to update packages via the command line (apt-get upgrade). For some reason, the GUI lock and terminal lock have always been separated.

To lock a package from apt-get upgrades, you have to 'hold' a package. Here is a link to the Community documentation that explains it. 
[https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages]("https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages")
Thanks for the info.  :D

---

### Post by theodorekon on 2011-11-28
> **drs305 said:**
> I was trying to find a way to lock the version of a package via Software Center since Synaptic seems out of fashion these days.  I was unable to find a way to do it.

The GUI method in previous versions has been to 'lock' the package via Synaptic. You may have to install Synaptic, but once you do, you can lock any package to the current version and I *think* that will stop the reminders. Try it, and if it still keeps reminding you, please report back.

Here is a link:

[http://ubuntuguide.net/lock-package-versionskeep-application-at-specific-version-in-ubuntu]("http://ubuntuguide.net/lock-package-versionskeep-application-at-specific-version-in-ubuntu")


It worked for me too. Thanks a lot!!

---

