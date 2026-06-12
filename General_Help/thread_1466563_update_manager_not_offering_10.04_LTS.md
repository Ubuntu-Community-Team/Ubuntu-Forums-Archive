---
title: "update manager not offering 10.04 LTS"
date: 2010-04-30
forum: General Help
---

### Post by itiswhatitis on 2010-04-30
I am running the 10.04 RC/Beta.  When I run update manager, it is not offering me the latest version.  I tried update-manager -d, which did not offer it either.

I was told that I would be able to upgrade from the beta/rc to the final version when it came out...  Am I missing something?

Thanks,

IIWII

---

### Post by Peter09 on 2010-04-30
Your missing nothing, the Ubuntu RC is to all intents and purposes the final release, there may have been a few tweaks but obviously none needed by your installation.
 
Sit back, relax, enjoy :)

---

### Post by maddg3241 on 2010-04-30
hit alt f2 the type ```
update-manager -d
```

---

### Post by philinux on 2010-04-30
> **maddg3241 said:**
> hit alt f2 the type ```
update-manager -d
```

He's already running 10.04

update-manager -d upgrades to the next release. Seeing as that would be 10.10 maverick meerkat, it doesn't exist yet.

This code or update manager is all he needs.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by itiswhatitis on 2010-04-30
Okay, I understand.  The teeny tiny package update it did last night was all that needed to change.  Just checked by about Ubuntu under system and it says I am LTS.  :-)

Thank you for the clarification.

---

