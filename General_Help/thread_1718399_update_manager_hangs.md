---
title: "update manager hangs"
date: 2011-03-31
forum: General Help
---

### Post by hangle on 2011-03-31
i have been running version 10.10 for a few months, and the update manager has worked until a few days ago. it now lists the files that will be installed but when i activate the 'install update' button, the system hangs.  i eventually have to kill the manager process.

i was wondering whether or not to re install the manager with: sudo apt-get install update-manager-core

or do i uninstall the manager before i install it?

or is there a better solution to the problem?


thanks

---

### Post by plucky on 2011-03-31
> **hangle said:**
> i have been running version 10.10 for a few months, and the update manager has worked until a few days ago. it now lists the files that will be installed but when i activate the 'install update' button, the system hangs.  i eventually have to kill the manager process.

i was wondering whether or not to re install the manager with: sudo apt-get install update-manager-core

or do i uninstall the manager before i install it?

or is there a better solution to the problem?


thanks

What happens if you run from a terminal ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hangle on 2011-03-31
sudo apt-get update && sudo apt-get upgrade

the apt ran successfully.  i did not realise that the update manager 
can be executed from the command line.
thanks for the help.   i am anxious to see if system-->update-manage will
run the next time i received a new batch of updates.  in any case i have
the apt commands to fall back on.

---

