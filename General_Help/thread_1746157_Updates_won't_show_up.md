---
title: "Updates won't show up"
date: 2011-05-01
forum: General Help
---

### Post by Teraspes on 2011-05-01
Hi!

I installed Ubuntu 11.04 beta 2 a week ago. And now I'm not sure if the update manager still works. I'm not even sure if the system has updated to the release version of Ubuntu. I get very few updates (none?) nowadays, compared to earlier when I had new updates every day. If I visit [https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/%7Echromium-daily/+archive/ppa") I can see that version 13.xxxx is the latest version, however in Synaptic Package  Manager it says that 11.xxx is the latest version and that it's already installed. Can anybody explain why it's like this? :S

---

### Post by garvinrick4 on 2011-05-01
> **Teraspes said:**
> Hi!

I installed Ubuntu 11.04 beta 2 a week ago. And now I'm not sure if the update manager still works. I'm not even sure if the system has updated to the release version of Ubuntu. I get very few updates (none?) nowadays, compared to earlier when I had new updates every day. If I visit [https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/%7Echromium-daily/+archive/ppa") I can see that version 13.xxxx is the latest version, however in Synaptic Package  Manager it says that 11.xxx is the latest version and that it's already installed. Can anybody explain why it's like this? :S You get the stable version of Chromium in Ubuntu and or you can install the daily build of chromium thru ppa. There has only been a few updates this week at all.
Some mirrors do not get updates as quick as others see attached link for Ubuntu mirrors I do not know which one you have but you can look. If you want to for anymore updates at command line:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
you can use above at this time but do not use it when a new version comes out in beta you just might get dist-upgraded to 11.10 just use upgrade and not dist-upgrade.
Using your update-manager in GUI is always easy but never use partial upgrades when advised in update-manager tends to make a mess of things. Here is your Mirror link can
change in software sources to new mirror if want to.
[Mirrors of Ubuntu : Ubuntu]("https://edge.launchpad.net/ubuntu/+archivemirrors")

---

### Post by Teraspes on 2011-05-01
I have added the Chromium Daily PPA, and when I type in "sudo apt-get update && sudo apt-get dist-upgrade" in the terminal, it results with nothing. I checked out the link with mirrors and tried some mirrors in my update manager, but it won't find any new updates.

---

### Post by garvinrick4 on 2011-05-01
> **Teraspes said:**
> I have added the Chromium Daily PPA, and when I type in "sudo apt-get update && sudo apt-get dist-upgrade" in the terminal, it results with nothing. I checked out the link with mirrors and tried some mirrors in my update manager, but it won't find any new updates.
 The mirrors have different up to date, some a week behind, some 2 days behind, some current. 
Some with larger band widths 100 meg, I gig, 2 gig, 10 gig.
If you have used an up to date mirror than you got all your updates. 
It will be a bit before some more updates all the people involved in that process are going to take a little break. At least I hope they do, it is always a rush for them to work on a 6 months schedule for a new version. Some distro's come out with new versions once in a blue moon or so. In about 3 weeks to a month 11.10 will start up.

---

### Post by garvinrick4 on 2011-05-02
> I have added the  Chromium Daily PPA, and when I type in "sudo apt-get update &&  sudo apt-get dist-upgrade" in the terminal, it results with nothing. I  checked out the link with mirrors and tried some mirrors in my update  manager, but it won't find any new updates. 	  	10 Hours Ago 12:53 PM If you want to use the dailys from the ppa it is different version
from one you get through your Ubuntu software center. Uninstall the one in Ubuntu software center and after installing ppa and key:
```
sudo apt-get update
```
```
sudo apt-get install chromium-browser
```

[http://www.techdrivein.com/2010/02/install-chromium-web-browser-in-ubuntu.html](http://www.techdrivein.com/2010/02/install-chromium-web-browser-in-ubuntu.html)
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)
Notice in ppa and ubuntu software center the different version numbers of chromium.

---

