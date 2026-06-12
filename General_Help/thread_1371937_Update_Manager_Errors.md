---
title: "Update Manager Errors"
date: 2010-01-04
forum: General Help
---

### Post by Monk! on 2010-01-04
When I try to install security updates with update manager I get two errors. E: dpkg was interupted. You must manually run 'sudo dpkg--configure-a' .

When I tried to run it the reply was "command not found"

Second error E: _cache->open ( ) failed. please report.

Is there a fix or would uninstalling and reinstalling update manager be easier?

Thanks

---

### Post by warfacegod on 2010-01-04
Try uninstall/reinstall first. Can you update with terminal?

---

### Post by Monk! on 2010-01-04
I don't know how to use terminal to update. Is it intuitive or do I need specific commands?

I do understand uninstall/reinstall however. If that wouldn't impact anything ellse I would like to try that.

---

### Post by warfacegod on 2010-01-04
```
sudo apt-get update
```

```
sudo apt-get install
```


I *think* that's it. The top one will find them anyway.


When you uninstall with Add/Remove it will tell you if doing this will mess up something else and tell you to do it in Synaptic.

---

### Post by Monk! on 2010-01-04
Thanks! I'll try these.

---

### Post by phreakphish on 2010-01-04
Hey,

I'm a fairly new user and I'm getting an Error when I try to use Update Manager, add/remove and Synaptic.

Error reads:

'E:Type '\u00e2\u0080\u0098deb' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

This happened when I tried to install a simple third party application "Blueman", a bluetooth manager.

Anyway, any help would be good. Thanks. Ubuntu 9.04; Sony Vaio Notebook.

---

### Post by phreakphish on 2010-01-04
I've also tried in terminal with the same resulting error.

---

### Post by MelDJ on 2010-01-04
> **Monk! said:**
> When I try to install security updates with update manager I get two errors. E: dpkg was interupted. You must manually run 'sudo dpkg--configure-a' .

Thanks

it should be sudo dpkg --configure -a

---

