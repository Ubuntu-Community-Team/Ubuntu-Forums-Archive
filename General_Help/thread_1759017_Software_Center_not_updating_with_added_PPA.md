---
title: "Software Center not updating with added PPA"
date: 2011-05-15
forum: General Help
---

### Post by ryanferreri on 2011-05-15
Today I tried adding several pieces of software using PPAs. I was able to add the PPA through "Software Sources" in the Software Center Edit menu. One I added a PPA, it wold show a running task for the update, but when I search for the software I want to get from the PPA in software center, it does not show up in the search results. However, I CAN add the software through the command line using apt-get.

For example, to add the QtQr application, I added ppa:qr-tools-developers/qr-tools-stable to Software Sources, and searched for 'qtqr.' There were no results. But I was able to 'sudo apt-get install qtqr' and it installed fine.

Am I missing a step if I want to install stuff from new PPAs in Software Center?

---

### Post by lindsay7 on 2011-05-15
You may need to run the following in the terminal

sudo apt-get upgrade
sudo apt-get update

this will get your system current and you can look for the software.

---

### Post by ryanferreri on 2011-05-15
I tried exiting Software Center and going back in, and running apt-get update (which Software Center does automatically after you add a software source, hence the running update task). Apt-get upgrade checks for updates to installed software and prompts for installation; that's not what we're looking for here. I just want to know if there's a step I'm missing here, inside Software Center, that should allow for searching for a software package in a PPA that was just added before I submit a bug.

---

