---
title: "Help with programs"
date: 2012-07-16
forum: General Help
---

### Post by cano1362 on 2012-07-16
I log into Chrome + effects and try to open software center and get the message... the package lists or status file could not be parsed or opened. Can anyone help me, new to Ubuntu. Thanks

---

### Post by searchfgold6789 on 2012-07-16
[LIST=1]
[*]Open a Terminal Window.
[*]Copy and paste this command into the window:```

sudo rm /var/lib/apt/lists/* -vf
```

[*]Press Enter to run the command.
[*]Type in your password, which will not be visible, and press enter.
[*]Once finished, enter in this command:```
sudo apt-get update
``` You should see lines of code as package information downloads.
[*]You should no longer receive the error message.
[/LIST]
Explanation:
Ubuntu stores the information for software packages, like the names, descriptions, etc., locally on the system in cache files. Yours became corrupt somehow and need to be downloaded again.

---

