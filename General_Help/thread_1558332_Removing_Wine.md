---
title: "Removing Wine"
date: 2010-08-22
forum: General Help
---

### Post by JollyJohn on 2010-08-22
Hi
How do I remove all traces of Wine?
I have installed Ubuntu 8.04 - suits my hardware - and imported settings from Mint5 which included a non working reference to wine and MS Money.  I wish to delete all traces of Wine and reinstall.
Thanks

---

### Post by claracc on 2010-08-22
This thread can help : [http://ubuntuforums.org/showthread.php?t=561606](http://ubuntuforums.org/showthread.php?t=561606)

---

### Post by sikander3786 on 2010-08-22
Hi. Run these commands

```

sudo apt-get remove --purge wine

```

```

rm -r ~/.wine

```

Or alternatively go to Synaptic, search for Wine, right click and Mark for complete removal and Apply.
Then in you home directory, search for hidden .wine folder and delete it.

Regards.

---

### Post by JollyJohn on 2010-08-22
Thanks.

---

