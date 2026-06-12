---
title: "Pidgin randomly hogging resources, freezes when doing so"
date: 2011-02-09
forum: General Help
---

### Post by theyain on 2011-02-09
During random moments, pidgin will suddenly use up all of my processor, a large chunk of my ram (20% - 25% of 2 GB), and will become completely unresponsive.  This lasts for maybe four or five minutes then returns to normal.

Pidgin doesn't have any kind of terminal output when ran in a terminal, so I have no data to use that is of any help.

Does anyone have any clue as to what could possibly be happening?

---

### Post by theyain on 2011-02-10
Bump

---

### Post by theyain on 2011-02-12
Bump

---

### Post by williamts99 on 2011-02-12
> **theyain said:**
> During random moments, pidgin will suddenly use up all of my processor, a large chunk of my ram (20% - 25% of 2 GB), and will become completely unresponsive.  This lasts for maybe four or five minutes then returns to normal.

Pidgin doesn't have any kind of terminal output when ran in a terminal, so I have no data to use that is of any help.

Does anyone have any clue as to what could possibly be happening?

I would install the latest version from the ppa linked on the official Pidgin.im site as it has fixed some 'issues' like memory leaks.

From the command line:
```
sudo apt-add-repository ppa:pidgin-developers/ppa
```

Then update and upgrade:
```
sudo apt-get update ; sudo apt-get upgrade
```

---

### Post by theyain on 2011-02-15
Oddly enough, I added the PPA then ran update and upgrade, but none of the packages that installed were related to pidgin (just a google chrome update)

---

### Post by williamts99 on 2011-02-15
What version of pidgin is installed on your system?  Are you still using 10.04 and do you have any other repositories added?

And you can see the latest version in the PPA on the following website:
[https://launchpad.net/~pidgin-developers/+archive/ppa/](https://launchpad.net/~pidgin-developers/+archive/ppa/)

---

