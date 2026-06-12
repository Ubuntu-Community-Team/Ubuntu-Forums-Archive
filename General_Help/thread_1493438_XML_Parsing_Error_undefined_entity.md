---
title: "XML Parsing Error: undefined entity?"
date: 2010-05-25
forum: General Help
---

### Post by moore.bryan on 2010-05-25
Using Mozilla's Daily PPA and getting this when I try and launch any Prism program:
```
XML Parsing Error: undefined entity
Location: chrome://webrunner/content/webrunner.xul
Line Number 58, Column 5:    <command id="cmd_saveImage" label="&saveImage.label;" oncommand="WebRunner.doCommand(this.id);"/>
----^
```
Any ideas?

---

### Post by PomCompot on 2010-05-26
Same error for me&#8230; No idea of solution.

---

### Post by moore.bryan on 2010-05-26
Sorry for you, too. Updates this morning, ~5:30am EST, yielded no fix.

---

### Post by n2o-Gr55 on 2010-05-26
Hey, i had the same problem up until a few minutes ago. A fresh reinstall worked fine.

I am not sure if it was because i was using Namoroka (firefox daily build) or some other odd reason, but a fresh firefox install worked fine- addons intact too.

Heres a code for quick copy pasting ;)
```
sudo apt-get remove firefox -y; sudo apt-get remove prism; sudo apt-get install firefox; sudo apt-get prism
```Cheers,
n2o-Gr55

---

