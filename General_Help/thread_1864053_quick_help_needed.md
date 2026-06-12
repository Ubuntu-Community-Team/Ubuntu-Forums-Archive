---
title: "quick help needed"
date: 2011-10-18
forum: General Help
---

### Post by flipper T on 2011-10-18
i've been silly

enabled xorg ppa in ubuntu tweak, now when i boot, i get just a blank screen.

i can ctrl alt f1 to get a terminal, but thats all (running live cd to type this)

so i need to remove whatever drivers i have messed up, boot in some safe mode, then reinstall standard drivers....don't know how


quick answer if possible   :)

---

### Post by pqwoerituytrueiwoq on 2011-10-18
use the ppa-purge package to undo it
hint: recovery mode is useful
```
sudo apt-get install ppa-purge; sudo ppa-purge **ppa:xorg-edgers/ppa**
sudo apt-get update;sudo apt-get upgrade
```i assume [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") is the ppa that Ubuntu Tweak added upon your request

---

### Post by ajgreeny on 2011-10-18
When I did more or less the same thing a while ago, I tried just reinstalling them from the cli, having removed  the **/etc/apt/sources.list.d** entry for the xorg edgers repository.  That did not seem to work, so I removed xserver-xorg with all its dependencies from the Ctrl+Alt+F1 cli and then reinstalled them all.

A quick reboot put everything back to normal.  This was on 10.04, with an old ATI radeon 9200SE card.  Very easy to do if you know how, so don't be afraid of the job;  it took only about 5 mins to do.

---

