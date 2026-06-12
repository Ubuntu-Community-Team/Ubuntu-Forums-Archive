---
title: "Two battery icons on bar"
date: 2011-10-14
forum: General Help
---

### Post by fritz269 on 2011-10-14
Anyone know how to remove the second battery icon on the top bar?

---

### Post by Bubble32 on 2011-10-16
Same problem here...anyone?!\.

---

### Post by the-oggy on 2011-10-16
Same with me, but when I revert all the settings to default ones (delete .gnome2, .gconf, and some other folders from home dir) only one icon remains... But when I change theme or do any change other icon reappears and is damn ugly...

EDIT: disable second indicator by blacklisting all old indicators with [FONT=Courier New]

[/FONT]```
[FONT=Courier New]gsettings set com.canonical.Unity.Panel systray-whitelist "['']"
```[/FONT]

---

