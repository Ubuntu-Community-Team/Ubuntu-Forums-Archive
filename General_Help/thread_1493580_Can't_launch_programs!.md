---
title: "Can't launch programs!"
date: 2010-05-26
forum: General Help
---

### Post by farbre on 2010-05-26
I have a strange problem. My system will run normally for some time, and then I can no longer launch some programs. I checked the System Monitor, and the affected processes appear with the Waiting Channel "unix_wait_for_peer". I can't even open the terminal!

I also can't shut down properly because the "Quit" dialog is blank. However, if I do nothing it does shut down after 60 seconds, and upon restart all is normal again (until next time...).

Any ideas?

---

### Post by dino99 on 2010-05-26
look at errors into:

- .xsession-errors : unhide it into /home with the menu
- system admin log viewer

clean your system:

install gconf-cleaner with synaptic (run it, yes to all)

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by scrapmetal on 2010-05-26
Bad Post -sorry
Cut and pasted into terminal - working
Can you install
gconf-cleaner
from command line.

Getting error messages in 9.04.  LTS

Add/Remove and Synaptic

E: dpkg --- configure -a
E: cache->open(failed, please report

Simple instruction would be appreciated.
Thanks

---

### Post by dino99 on 2010-05-26
> **scrapmetal said:**
> Can you install
gconf-cleaner
from command line.

Getting error messages in 9.04.  LTS

Add/Remove and Synaptic

E: dpkg --- configure -a
E: cache->open(failed, please report

Simple instruction would be appreciated.
Thanks

look at post #2 above

---

