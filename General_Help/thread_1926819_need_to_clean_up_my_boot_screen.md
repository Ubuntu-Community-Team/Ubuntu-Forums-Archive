---
title: "need to clean up my boot screen"
date: 2012-02-16
forum: General Help
---

### Post by silvama11 on 2012-02-16
I used Wubi to install Ubuntu 11.x (the latest distro)in a dual boot configuration with Win 7. I wasn't happy with the size of the Ubuntu OS so I used Wubi to delete it. So all the files are gone and I figured that my boot would go directly into Windows as it did prior to the install of Ubuntu.
It did not! 
I saw both Windows and Ubuntu on the screen (standard dual boot menu) I tried Ubuntu first and got a message saying that Windows could not ...use a rescue disc blah blah blah. I restart the machine choose Windows and the system slides right into windows no prob works as usual. 
So my question how do I get the Ubuntu entry off my boot screen. I know that if I don't clear it up  *will have 2 entries for Ubuntu and it could get messy.:confused:*

---

### Post by bcbc on 2012-02-17
Go to an administrative command prompt:
```
bcdedit
```
This outputs your boot entries. Look for the Ubuntu entry and note the {GUID}.

```
bcdedit /delete {GUID}
```

e.g. the ubuntu entry looks like this:
```
Real-mode Boot Sector
---------------------
identifier              {b5585177-4e2e-11e1-8d6a-005056c00008}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu
```

You would enter:
```
bcdedit /delete {b5585177-4e2e-11e1-8d6a-005056c00008}
```

---

### Post by silvama11 on 2012-02-18
[SIZE="4"]Thanx that did the trick.[/SIZE]

---

