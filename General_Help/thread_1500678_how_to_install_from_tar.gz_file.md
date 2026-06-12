---
title: "how to install from tar.gz file"
date: 2010-06-03
forum: General Help
---

### Post by DrScum on 2010-06-03
I need to install a non free firmware package in lucid but don't know how. Can't use apt or software sources since the firmware is from the wlan card and cable connection would be a drag.

How do I install from a tar.gz file? I did search and I did follow numerous tutorials but they didn't work. Obviously things changed in lucid.

---

### Post by WorMzy on 2010-06-03
You don't. That's just an archive. You need to:

[LIST]
[*]Extract the contents of the archive
[*]Run a terminal and browse to the newly created folder
[*](Optionally, if a configure file has been provided) run "./configure"
[*]Run "make"
[*]Finally (if you don't get any errors) run "sudo make install".
[/LIST]

---

### Post by philinux on 2010-06-03
> **DrScum said:**
> I need to install a non free firmware package in lucid but don't know how. Can't use apt or software sources since the firmware is from the wlan card and cable connection would be a drag.

How do I install from a tar.gz file? I did search and I did follow numerous tutorials but they didn't work. Obviously things changed in lucid.

[http://www.psychocats.net/ubuntu/installingsoftware#lastresorts](http://www.psychocats.net/ubuntu/installingsoftware#lastresorts)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by bodhi.zazen on 2010-06-03
> **DrScum said:**
> I need to install a non free firmware package in lucid but don't know how. Can't use apt or software sources since the firmware is from the wlan card and cable connection would be a drag.

How do I install from a tar.gz file? I did search and I did follow numerous tutorials but they didn't work. Obviously things changed in lucid.

First it helps if you are more specific. What are you trying to install and what problem did you have ? What error message did you get ? Did you install the dependencies, if any ? Did you install build-essential ?

You do not install anything from a tar.gz. tar.gz is an archive. Archives can contain anything. Firefox and songbird for example contain binaries so nothing to "install". Other archives contain install scripts. Yet other archive are source code which then needs to be compiled.

You extract the contents and read the README. 

Without additional information from you, really can not give you more specific assistance, could be any number of problems.

---

