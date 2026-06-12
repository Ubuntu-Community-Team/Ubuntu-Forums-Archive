---
title: "Synce"
date: 2009-11-12
forum: General Help
---

### Post by maarten@me50.net on 2009-11-12
can't make Synce work on my computer. trying to sync my HTC touch HD with win 6.1

error:

** (process:31195): CRITICAL **: synce_info_from_hal: Failed to initialise hal context: (null): (null)
process 31195: Attempt to remove filter function 0xd0e600 user data 0x880fa00, but no such filter has been added
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'

yours
maarten

---

### Post by gurukreff on 2010-05-12
I have the exact same problem. Synce used to work for me with no problems in Karmic, i followed the same instructions for lucid (those that are posted in the Synce wiki) and i get almost the same output than maarten:


```
marko@marko-desktop:~$ synce-pls

** (process:4726): CRITICAL **: synce_info_from_hal: Failed to initialise hal context: (null): (null)
process 4726: Attempt to remove filter function 0x7f0302adad90 user data 0xedfe90, but no such filter has been added
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'
```


Is there any way to fix this?

Thanks

---

