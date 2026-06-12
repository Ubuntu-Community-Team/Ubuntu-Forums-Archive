---
title: "ubuntu software center not working"
date: 2012-01-30
forum: General Help
---

### Post by dsuresh on 2012-01-30
hi, 

   ubuntu software center & synaptic package not working.. ....
cannot install any software..please help


[U]error msg  : package dependencies cannot be resolved
this error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.[/U]

i have tried commandlines..
sudo apt-get install
sudo apt-get clean or remove ..etc...

---

### Post by sikander3786 on 2012-01-30
From the Terminal please try these commands and also post their outputs:

```
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get upgrade
```

While posting the outputs, please use the code tags by clicking the # icon in post menu and pasting the text in between the generated code tags.

---

### Post by dsuresh on 2012-01-30
thanks for ur reply..... but i reinstall the ubuntu.....thanks...

---

