---
title: "Open office has gone belly up!"
date: 2010-06-19
forum: General Help
---

### Post by old_dog on 2010-06-19
have deleted and tried to reload Open-Office but it crashes out with "dependencies failing" what is the cleanest way to get rid of the original and get a clean install?
Cheers Guys

---

### Post by Linuxforall on 2010-06-19
sudo apt-get --purge remove openoffice* and then reinistall.

---

### Post by aviedw on 2010-06-19
I would assume that one of the better ways to ensure that you've completely deleted a program is to use the purge command this would remove packages and config files.

edit: Beat me to it

---

### Post by beowulf1416 on 2010-06-19
using ubuntu software center:
go to Applications - Ubuntu Software Center
Find OpenOffice, its in the Office category, click "Remove".

---

### Post by wilee-nilee on 2010-06-19
I would just remove all things open office from synaptic rather then the purge, then go to home and hit ctrl-h to show hidden files and delete the  .openoffice.org file. OO is finicky you have to remove that file in home.

---

### Post by Hagar Delest on 2010-06-19
Don't trust the Software Center to remove OOo. Do that from Synaptic indeed. Then install the Sun/Oracle version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

