---
title: "firefox 4, ctrl-q shortcut closing"
date: 2011-05-21
forum: General Help
---

### Post by Gatemaze on 2011-05-21
Hi,

ctrl-q closing firefox being next to ctrl-w closing tab shortcut is one of the most annoying things firefox4. Had a look on [http://ubuntuforums.org/showthread.php?t=1538388&highlight=firefox+ctrl-q](http://ubuntuforums.org/showthread.php?t=1538388&highlight=firefox+ctrl-q) but it does not really work with firefox from what I tried. Any clues that do not involve installing a plugin? Even a warning that you are about to close multiple tabs would be ok for me. Disabling completely would be ideal.

Thanks.

---

### Post by mikewhatever on 2011-05-21
All Firefox versions have a 'Quit warning setting' turned on by default. If you turned it off and want to revert the change, type [noparse]about:config[/noparse] in the address bar, search for 'browser.showQuitWarning', and change it to 'true'.

---

### Post by Gatemaze on 2011-05-22
> **mikewhatever said:**
> All Firefox versions have a 'Quit warning setting' turned on by default. If you turned it off and want to revert the change, type [noparse]about:config[/noparse] in the address bar, search for 'browser.showQuitWarning', and change it to 'true'.

It is actually false by default in firefox 4. But setting it to true does the job. Thanks.

---

### Post by harun3d on 2012-07-05
[LIST=1]
[*]Go to System -> Preferences -> Keyboard settings
[*]Click Add
[*]Give it a name like *fake setting* and enter /bin/false as command. Apply your changes.
[*]Click on 'Disabled' and press Ctrl+Q.
[/LIST]

---

### Post by harun3d on 2012-09-28
> **harun3d said:**
> 
[LIST=1]
[*]Go to System -> Preferences -> Keyboard settings
[*]Click Add
[*]Give it a name like *fake setting* and enter /bin/false as command. Apply your changes.
[*]Click on 'Disabled' and press Ctrl+Q.
[/LIST]

If you press Ctrl+Q it quits the keyboard settings also instead of putting ctrl q as shortcut key.

also: alt+f2> gconf-editor> apps metacity global keybinding>fake shortcut> <Control>q is not a solution

also: firefox settings warn on close active is not a solution. it does not warn. it quits.


any other solution?

---

