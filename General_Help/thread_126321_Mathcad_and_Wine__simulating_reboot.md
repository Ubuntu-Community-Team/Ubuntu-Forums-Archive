---
title: "Mathcad and Wine / simulating reboot"
date: 2006-02-06
forum: General Help
---

### Post by dizzy1234 on 2006-02-06
Hi,

I need to install Mathcad for Uni but I've never really used Wine before and I don't have a windows box at the minute. According to WineHQ MathCad should work, but I'm having a few problems.

First is there any way (or need...) to simulate a windows reboot? According to the documentation I was sent, the installer will need to reboot once or even twice during the install process, but I'm not sure how to simulate this. A programme I used to install IE a while back did this fairly well.

Second, I'm getting an error reading "1605: Unable to create InstallDriver instance". I assume this may be something to do with the lack of reboot but I don't know. I had to forcequit a previous attempt at install so that might have had something to do with it.

Cheers
Nick

---

### Post by dcstar on 2006-02-06
[QUOTE=dizzy1234]Hi,

I need to install Mathcad for Uni but I've never really used Wine before and I don't have a windows box at the minute. According to WineHQ MathCad should work, but I'm having a few problems.

First is there any way (or need...) to simulate a windows reboot? According to the documentation I was sent, the installer will need to reboot once or even twice during the install process, but I'm not sure how to simulate this. A programme I used to install IE a while back did this fairly well.

Second, I'm getting an error reading "1605: Unable to create InstallDriver instance". I assume this may be something to do with the lack of reboot but I don't know. I had to forcequit a previous attempt at install so that might have had something to do with it.

Cheers
Nick[/QUOTE]

The winetools utility has a "Simulate reboot" function, but you will have to download and install this yourself as it is no longer in the Winehq repository as a .deb package.

---

