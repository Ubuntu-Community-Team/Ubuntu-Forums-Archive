---
title: "Saving List of Progs?"
date: 2009-08-05
forum: General Help
---

### Post by oaxacamatt1 on 2009-08-05
Greetings all,

Does anybody remember which command to use to write / save a list of programs that I have loaded on my Ubuntu box.  I thought it might be the 'apt-get' command but the man page does mention anything like that. 
 
Cheers,
M

---

### Post by stillious on 2009-08-05
```
dpkg --get-selections > software
```

This will give you an output file called software with the list of programs.

---

### Post by oaxacamatt1 on 2009-08-06
Hey maciasoo,
yea the info you gave was on target but used it fully, in a sense.  I also want to use this list to re-install the progs that had before.  So i haven't looked into the 'converse.'  in other words how to use the list to re-install.
cheeers,
m

---

### Post by philinux on 2009-08-06
In synaptic you can do it. File save markings as. Tick the Save Full state.

Or as mentioned above.
[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

This is old but the commands are relevant. Needs sudo.

Have a search around.
[http://ubuntuforums.org/showthread.php?t=169062](http://ubuntuforums.org/showthread.php?t=169062)

---

