---
title: "Apt-get upgrade showing different packages then Update Manager"
date: 2010-11-06
forum: General Help
---

### Post by e24ohm on 2010-11-06
Folks:
The strangest thing is going on. I just did a fresh install of 9.10; however, apt-get upgrade returns different results then Update Manger found under System > Administration > update Manager.

In addition, the apt-get upgrade method excludes a few upgrades from being installed. These upgrades are bind9, and a few for FireFox.

Has anyone run into this issue recently?

---

### Post by cipherboy_loc on 2010-11-06
When you run apt-get update does it give you errors about missing GPG keys? Sometimes when I update (sudo apt-get update) the repository info (this does not upgrade any of the installed programs) it gives me errors about missing GPG keys. Open up a terminal (alt+f2 and in the box type gnome-terminal (assuming you are using Ubuntu and not Kubuntu)) and in that box type sudo apt-get update. Post the output of that command.

Why I am wondering about this is because update manager can show different packages if some repositories do not have GPG keys. Does this problem happen in Synaptic? Try opening it up (System -> Administration -> Synaptic) and comparing the three lists. I have the feeling that missing GPG keys might be your issue, but I could be wrong.


Cipherboy

---

### Post by dcstar on 2010-11-06
> **cipherboy_loc said:**
> When you run apt-get update does it give you errors about missing GPG keys? Using update manager I have been able to "force" updates (with missing keys) while apt-get upgrade would not allow me to. (Or visa versa). 


Cipherboy

apt-get upgrade <> apt-get update. Someone is seriously confused here.

---

### Post by cipherboy_loc on 2010-11-06
Edited.

---

### Post by e24ohm on 2010-11-06
<Update on issue>

After submitting to defeat, I was forced to use the GUI and was able to use the Update Manager to install the packages, which were not able to be install via cli by sudo apt-get upgrade. Unfortunately, I did not check which packages that are in question; however, I did notice Bind9, and a good number of Firefox  - I mentioned this earlier.

The only thing I can think of – I was using the Terminal app via Gnome. I wonder if I dropped into a virtual console would make a difference.

---

