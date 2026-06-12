---
title: "home folder locks up computer"
date: 2010-04-14
forum: General Help
---

### Post by kmrs75 on 2010-04-14
everytime i try to navigate to the home folder the pc lockes up. the mouse will move but the screen is locked upi have to restart and ideas

---

### Post by gzarkadas on 2010-04-15
Look at your logs to see what messages show up when you try to access the home folder.

Also, does Ctlr+Alt+F1 works? do you get a login screen? If yes, you can login and issue the `top', `ps', `lsof' etc. commands to try spot the process that delays so much.

If your /home is in a local partition, check whether it is damaged. If it is in a remote share, check if communications are ok (interfaces are up, no firewall rules are blocking any port used by the sharing protocol,etc.).

---

