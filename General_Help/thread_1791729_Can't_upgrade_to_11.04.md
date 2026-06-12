---
title: "Can't upgrade to 11.04"
date: 2011-06-27
forum: General Help
---

### Post by lampo on 2011-06-27
Hi everyone, i've a problem with the upgrade from Kubuntu 10.10 to 11.04.
I tried to upgrade just a week after the release, everything went well, except that after the first reboot the computer became irresponsive during the KDE splash screen. I then tried a couple of things (like updating or not updating, changing the settings of the session manager, do a new installation), but I couldn't get it working.
So, I decided to wait for some time, and indeed, when yesterday I downloaded, installed and upgraded Kubuntu 11.04 (installed beside my Windows and Kubuntu 10.10), everything worked the right manner.

Here is the problem: I can find no more the distribution upgrade option that KPackagekit offered me till a week ago! I've tried with apt-get update && apt-get dist-upgrade, and here is the result:

[INDENT]$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/INDENT]

I tried do-release-upgrade too, but without any result:

[INDENT]$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found[/INDENT]

Has someone an idea to get around this problem?
Thanks in advance.

---

