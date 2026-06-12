---
title: "udev rule not creating SYMLINK"
date: 2011-04-20
forum: General Help
---

### Post by mark_davis on 2011-04-20
Hello,

I'm looking for a little help with a udev rule that I'm trying to write. What I would like to do is every time a usb device is inserted to kick of a script that runs. I figured I would worry about the script later and just get it to create the symlink first to make sure my rule was right. 

My rule looks like this. The name of the rule is. 85-thumbdrive.rules and it is in /etc/udev/rules.d/

```
KERNEL=="sd*1", DRIVER=="usb-storage", SYMLINK+="ScanTron" 
```

We are using 10.04.2 LTS. Any help would be amazing!

---

