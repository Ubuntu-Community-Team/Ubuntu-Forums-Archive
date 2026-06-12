---
title: "cant upgrade from 10.04 to 12.04"
date: 2012-07-17
forum: General Help
---

### Post by JigglyWiggly_ on 2012-07-17
So i cant seem to ugprade
in update-manger 12.04 is not there
and if I do
sudo update-manger --dist-upgrade it says i am on the latest?

I do uname -r but i on on the 2.6.32 kernel...

do they test this stuff ever?

However if I put the setting to show all releases it will let me update to 10.10 which I certainly do not want to do.

Pretty much the same problem

[http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-10-04-to-12-04-lts](http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-10-04-to-12-04-lts)

---

### Post by claracc on 2012-07-18
Taken from [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS) :
> t is generally recommended that users of Ubuntu 10.04 LTS wait until the first point release, due in August, before upgrading.

To upgrade from 10.04 LTS on a desktop system before then, upgrade over the network with the following procedure.

    Start System/Administration/Software Sources
    On the Updates tab, set Show new distribution releases: to Long term support releases only, then press Close.
    Press Alt-F2 and type update-manager -d
        Click the Check button to check for new updates. If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.
        A message will appear informing you of the availability of the new release. Click Upgrade. 
    Follow the on-screen instructions. 

---

### Post by UltimateCat on 2012-07-18
claracc:

Do you have any clue as to why our member would not have update manager in his/her System>Admin>?

I'm wondering because I too have 10.04-

---

### Post by claracc on 2012-07-18
The 12.04 LTS will appear un update manager when 12.04.01 be released, more or less in august : [http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-10-04-to-12-04-lts](http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-10-04-to-12-04-lts)

---

### Post by JigglyWiggly_ on 2012-07-18
i guess i can wait ; /... since ubuntu distros are very rarely stable at release.

---

### Post by UltimateCat on 2012-07-18
> **claracc said:**
> The 12.04 LTS will appear un update manager when 12.04.01 be released, more or less in august : [http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-10-04-to-12-04-lts](http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-10-04-to-12-04-lts)

Confirmation is always good.  Thanks for the link:P

---

### Post by claracc on 2012-07-18
> Confirmation is always good. Thanks for the link

You are welcome

> i guess i can wait ; /... since ubuntu distros are very rarely stable at release. 

If you have fixed your proble, please mark the thread as solved with "thread tools" in the upper right part of the page.

---

