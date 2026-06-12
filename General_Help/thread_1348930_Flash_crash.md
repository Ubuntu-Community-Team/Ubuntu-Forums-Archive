---
title: "Flash crash"
date: 2009-12-07
forum: General Help
---

### Post by ALF102 on 2009-12-07
Well, this happen after I update, then restart:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

When I try to reinstall the package, it won't work.

---

### Post by CHaoSlayeR on 2009-12-07
I assume you are on karmic, so the plugin package is now called:
```
flashplugin-installer
```

Also you should issue a
```
sudo apt-get clean
```
to clean the local repository cache.

I hope this helps,

C]-[aoZ

---

### Post by gradinaruvasile on 2009-12-07
Open a terminal and type:
sudo apt-get purge adobe-flashplugin && sudo apt-get install flashplugin-installer

---

### Post by ALF102 on 2009-12-07
Ok, I've tried both ways and I get the follwing error:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

---

### Post by CHaoSlayeR on 2009-12-07
Retry purge with the force-flag (-f).

---

### Post by ALF102 on 2009-12-07
Should I type it like this?

 sudo apt-get purge adobe-flashplugin-f

Cuz I still get the same error

---

### Post by gradinaruvasile on 2009-12-07
sudo apt-get remove --purge -f adobe-flashplugin

---

### Post by ALF102 on 2009-12-07
alfy102@alfy102-laptop:~$ sudo apt-get remove --purge -f adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

---

### Post by ALF102 on 2009-12-07
Umm, does it help if I manually remove the plugin. If it does, how?

---

### Post by CHaoSlayeR on 2009-12-07
OK,

then try this:
```
sudo apt-get -m purge adobe-flashplugin
```

If this doesn't help tr to remove it with dpkg as it doesn't 'check' that much.

---

### Post by ALF102 on 2009-12-07
Nope still no luck, how do I remove it with dpkg

---

### Post by CHaoSlayeR on 2009-12-07
E.g.:
```
sudo dpkg -P adobe-flashplugin
```

---

### Post by ALF102 on 2009-12-07
dpkg: error processing adobe-flashplugin (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 adobe-flashplugin

---

