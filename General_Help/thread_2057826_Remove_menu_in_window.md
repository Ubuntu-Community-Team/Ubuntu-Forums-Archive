---
title: "Remove menu in window"
date: 2012-09-14
forum: General Help
---

### Post by daniellog on 2012-09-14
After an update I seem to have a menu bar appear in my my windows, how do I remove this?

[IMG]http://imageshack.us/a/img835/9783/screenshotfrom201209141.png[/IMG]

---

### Post by daniellog on 2012-09-17
Bump, anyone?

---

### Post by daniellog on 2012-09-17
Guess I'll have to reinstall then :/

---

### Post by Habitual on 2012-09-17
> **daniellog said:**
> Guess I'll have to reinstall then :/

No! 
try this...
Logout of the Desktop session and at the login dialog/prompt press Ctrl+Alt+F1 and login as yourself.
```

mv ~./config ~/.config.bak
mv ~/.gconf ~/.gconf.bak
exit
```

Then Ctrl+Alt+F7 and then login as yourself.
NOTE: This will reset your desktop settings to default settings.

---

### Post by daniellog on 2012-09-17
> **Habitual said:**
> No! 
try this...
Logout of the Desktop session and at the login dialog/prompt press Ctrl+Alt+F1 and login as yourself.
```

mv ~./config ~/.config.bak
mv ~/.gconf ~/.gconf.bak
exit
```

Then Ctrl+Alt+F7 and then login as yourself.
NOTE: This will reset your desktop settings to default settings.

It has reset my desktop but the two menu issue still remains. I think its some sort of gnome issue :S

---

### Post by Habitual on 2012-09-17
ouch. Sorry it didn't fix it.

---

### Post by daniellog on 2012-10-08
Bump, has anyone had this same issue? Still not resolved :/

---

