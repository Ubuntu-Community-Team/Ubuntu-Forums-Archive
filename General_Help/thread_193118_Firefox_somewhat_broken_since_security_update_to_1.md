---
title: "Firefox somewhat broken since security update to 1.5.0.4"
date: 2006-06-09
forum: General Help
---

### Post by Heavy-G on 2006-06-09
There appears to be an issue with the Firefox security update to 1.5.0.4.
I have just seen this problem on two computers who just updated a few minutes ago.

After the update, there appears to be an error in one of the configuration files. I noticed this problem when I tried to install a plugin. Just clicking the link to the .xpi file gives me the following:

```

XML Parsing Error: not well-formed
Location: chrome://mozapps/content/xpinstall/xpinstallConfirm.xul
Line Number 1, Column 1://mozapps/locale/extensions/update.properties"/>
^

```

Any hints on how to solve this?

---

### Post by ????? on 2006-06-09
Do you see that when getting other plugins/extensions?

---

### Post by Heavy-G on 2006-06-09
Indeed, clicking any link to any .xpi file pops up this error.

Edit: Sigh. Serious case of PEBKAC.
Seems that I forgot to close Thunderbird, which was running on another desktop, before restarting Firefox after the update.

Nevermind, case closed :)

---

