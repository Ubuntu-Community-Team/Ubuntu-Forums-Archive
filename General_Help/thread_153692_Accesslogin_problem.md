---
title: "Access/login problem"
date: 2006-04-01
forum: General Help
---

### Post by homersbrain on 2006-04-01
I had just been installing wine with automatix when it seemed to end suddenly. I used synaptic to download the remaining files and all seemed well. However, I soon discovered that I was unable to store anything anywhere on the hard drive. Even firefox would no longer start. I decided to restart the machine and now I cannot login as GDM reports there is no room on the drive. What on earth has happened? P.S. This has happened before and removing the .ICEauthority file made no difference whatsoever. I had to wipe the machine and start over again! This is driving me crazy!

---

### Post by homersbrain on 2006-04-02
Solved. Dropped down to console (ctrl+alt+F1) and then used:

'sudo apt-get clean'

to purge the root directory of whatever had appeared to fill it!

---

