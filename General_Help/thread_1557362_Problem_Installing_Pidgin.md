---
title: "Problem Installing Pidgin"
date: 2010-08-20
forum: General Help
---

### Post by ram2008 on 2010-08-20
[FONT="Verdana"][SIZE="3"]Earlier today I uninstalled Pidgin 2.71 and tried to go back to an earlier version but the OS (10.04) won't allow me to do that. I get the message that the package has unresolved dependencies.  It won't allow me to install the dependencies apart from Pidgin.  Someone suggested "sudo apt-get -f install pidgin" but that didn't help. Same message comes up about dependencies.  What do I do now?[/SIZE][/FONT]

---

### Post by techunit on 2010-08-20
try the following. ```
sudo apt-get autoremove
``` tell me if this helps at all. Then ```
sudo apt-get autoclean
``` this should give me a good starting point. After completing this please run ```
sudo apt-get update
``` please post what you get from the update command. in [code] brackets

---

### Post by ram2008 on 2010-08-20
Thanks for your response to my post.  I used "sudo apt-get autoremove" and that enabled me to re-install pidgin and its dependencies.  One thing I'm still not sure about and that is how to get rid of Pidgin 2.71 and get to perhaps 2.70 until the binaries for 2.73  have been posted.  I use the Pidgin ppa and it updated things back to 2.71 which has a number of bugs.  Although the Pidgin web site has a download link to 2.70, it doesn't actually lead you to that software.  In any case, I have a working version of Pidgin.  Thanks a lot for your help.

---

