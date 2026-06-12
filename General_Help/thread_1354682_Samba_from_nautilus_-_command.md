---
title: "Samba from nautilus - command"
date: 2009-12-14
forum: General Help
---

### Post by miroslav_karpis on 2009-12-14
Hi,
pls. do you know that what command is using nautilus for opening network files?

For example I would like to know that what is the command Nautilus is calling when I click on 'Places->Recent Documents->smb network document'

[COLOR="DarkRed"]I'm opening a document on a network (via samba)[/COLOR] - I have tried to open it from terminal but just can not figure out that how...

---

### Post by lightstream on 2009-12-14
In nautilus, you just need to specify the samba protocol in the location bar, like "smb://windowsshare/"

You can use this notation when opening a file from the command line too e.g

```
gedit smb://windowsshare/mydocument.doc
```

---

