---
title: "Need help locating Bloat"
date: 2010-06-04
forum: General Help
---

### Post by Razmear on 2010-06-04
My Ubuntu drive typically has about 4gb free, everything I download goes to a separate HD. This morning I get a message saying I have 750mb free. 

Computer Janitor says nothing to delete. I did fix an evolution glitch that wasn't emptying my trash but those 3000 messages only freed up about 250mb. 

Any ideas on where to look for this 3gb of bloat (or a best method)? I'll admit I'm not too diligent about system maintenance other than doing regular updates, and I'm more of a User than an Expert, so this 'bloat' could have been creeping up for some time with out me noticing. 

Thanks,
eb

---

### Post by wojox on 2010-06-04
Try downloading Bleachbit. It will clean up some bloat. You can run it as root and regular user.

```
sudo apt-get install bleachbit localepurge
```

---

### Post by dino99 on 2010-06-04
- uninstall what you dont use/need (in case, uninstall the metapackage ubuntu-desktop if needed)

- set the Firefox cache size down

- install gconf-cleaner and run it (yes to all)
- install bleachbit and use it as admin, but set your settings with caution (read comments about each setting you check)

- resize some partitions in case

---

### Post by Razmear on 2010-06-04
Thanks for the tip about BleachBit!
Found about 400meg in the Java Cache section (YaY Pogo) and going thru each section to see what else is lurking about. 

Much appreciated!

eb

update: 
Found 1.78 GB under System/Rotated Logs!!!

---

