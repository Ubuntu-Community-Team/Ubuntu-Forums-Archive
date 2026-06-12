---
title: "Removing Wubi/Ubuntu"
date: 2010-04-09
forum: General Help
---

### Post by Thunder X on 2010-04-09
so day before yesterday i install ubuntu using wubi. problem is, i couldn't get a internet connection. after several hours on another thread here, i mention i used wubi to install ubuntu, and it is recommended that i uninstall the wubi version and get the "real ubuntu". i uninstalled it, but when i reboot, i still get the boot screen with the windows/ubuntu option. seems from the get, ubuntu is a real pain. 

i'd appreciate the assist please.

---

### Post by ssulaco on 2010-04-09
What version of Windows are you running?
Take a look at this.
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by prodigy_ on 2010-04-09
You're jumping to conclusions and we all can do that. For example, once I had a trouble installing WinXP on my laptop. WinXP must be a real pain.

What's true is that operating systems are simply not meant to be installed in a Wubi-like way. And I sincerely doubt that Wubi will **ever** work flawlessly.

This being said, what exactly is the problem? You said you removed Ubuntu. Can you boot into Windows?

---

### Post by Thunder X on 2010-04-09
> **prodigy_ said:**
> You're jumping to conclusions and we all can do that. For example, once I had a trouble installing WinXP on my laptop. WinXP must be a real pain.

What's true is that operating systems are simply not meant to be installed in a Wubi-like way. And I sincerely doubt that Wubi will **ever** work flawlessly.

This being said, what exactly is the problem? You said you removed Ubuntu. Can you boot into Windows?

after uninstalling ubuntu, i still get the dual boot option screen. if i uninstalled it, i shpuld not be seeing this. no?

---

### Post by Thunder X on 2010-04-09
> **ssulaco said:**
> What version of Windows are you running?
Take a look at this.
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

i use windows xp. thanx for the link, but i just downloaded the ubuntu uninstaller and clicked run. nothing happened.

---

### Post by prodigy_ on 2010-04-09
> **Thunder X said:**
> after uninstalling ubuntu, i still get the dual boot option screen.

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by ssulaco on 2010-04-09
> **prodigy_ said:**
> 
What's true is that operating systems are simply not meant to be installed in a Wubi-like way. And I sincerely doubt that Wubi will **ever** work flawlessly.


I don't agree with you on that statement,Granted its not on its own partition,and an unintentional shutdown (Power outage)can bork your wubi install,but for someone wanting to play around with Ubuntu and doesnt care if they have to reinstall...its great,one of my wubi installs has been running for 6 months,with no hiccups.

---

### Post by steveneddy on 2010-04-09
> **prodigy_ said:**
> [http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

Or

try opening up a command line in windows and using the 

```
fixmbr
```

command to see how that works for you.

the **fixmbr** command means - **fix** **m**aster **b**oot **r**ecord - that should repair the issue.

If that doesn't do the trick, Put the Ubuntu CD back in the drive and restart the machine and install Ubuntu and get rid of XP.

EDIT:

From this link - which is from the links in my sig:

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Dual-Booting_Windows_and_Ubuntu)

it states:

> Wubi (Windows-based Ubuntu Installer), an officially supported dual-boot installer that allows Ubuntu to be run mounted in a virtual-disk within the Windows environment (**which can cause a slight degradation in performance**). Because the installation **requires an intact functioning Windows system**, it is recommended to install Ubuntu in this manner for **short-term evaluation purposes only**. [COLOR="Blue"]**A permanent Ubuntu installation should be installed in its own partition, with its own filesystem**[/COLOR], and should not rely on Windows.

---

