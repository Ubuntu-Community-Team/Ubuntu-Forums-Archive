---
title: "ndiswrapper"
date: 2005-02-08
forum: General Help
---

### Post by slow'puter on 2005-02-08
Does Ubuntu comes with ndiswrapper? If it does, what version?

---

### Post by trivialpackets on 2005-02-08
I'm not at home, so i can't see what version, but it does not come with it.  It is however in the apt-repositories, possibly the universe.  So enable the universe
in /etc/apt/sources.list

sudo apt-get update
sudo apt-cache search ndiswrapper
sudo apt-get install ndiswrapper-utils
sudo apt-get install ndiswrapper-source

That should do it I think.

---

### Post by slow'puter on 2005-02-08
Thanks!=D>

---

### Post by slow'puter on 2005-02-08
Hmm... I think that for apt-get, I need to be able to reach the internet.
 
 I have a .deb file for ndiswrapper, and a .tar. Which one to use?

---

### Post by jdodson on 2005-02-08
use the .tar, build it from source.  make sure to install the kernel-headers off the install cd.  the readme docs in the tar are very helpful.

---

### Post by slow'puter on 2005-02-08
Sorry for being a pain in the butt, but the ndiswrapper installation halted due to an error.
  
  I did, as root: modprobe ndiswrapper
  
  and got:
  
 FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-3-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invald module format.
  
  Where I went wrong. Please help! [img]http://www.ubuntuforums.org/images/smilies/eusa_boohoo.gif[/img]

---

