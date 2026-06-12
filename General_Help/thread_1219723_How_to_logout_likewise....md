---
title: "How to logout likewise..."
date: 2009-07-22
forum: General Help
---

### Post by t43m4n on 2009-07-22
How do I make it so Likewise will logout whenever a user logs out or shuts down the PC? Right now, everytime I log in ubuntu, it automatically connects to the domain.

---

### Post by jerrrys on 2009-07-22
has it just taken control of your browser?  if so this should fix it if your running FF

[ATTACH]122046[/ATTACH]

---

### Post by t43m4n on 2009-07-22
Im sorry if my question did not sound right but I think you did not get it. LIKEWISE is a program that connects linux to a windows domain. Now the thing is, there are times when a different user uses another PC, so in this case he/she should log in into the domain again (via likewise). The problem is, everytime a user logs in UBUNTU, LIKEWISE automatically starts and connects the previous user to a domain not allowing the new user to log in to the windows domain. 

Is there a setting on how I can deactivate LIKEWISE on startup?

---

### Post by jerrrys on 2009-07-23
well i gave it a good look and all i could find is  **sudo domainjoin-cli leave**  that worked on a Win2k3 

post #1

[http://ubuntuforums.org/showthread.php?t=812530](http://ubuntuforums.org/showthread.php?t=812530)

good luck

---

