---
title: "Discovered a stupid problem with FAT32 installed ubuntu"
date: 2009-08-21
forum: General Help
---

### Post by dgrafix on 2009-08-21
I have a netbook with ubuntu on it. It ran out of battery and now when i start it it starts a fsck check with no way of escaping it and finds errors.  
It says fsck must be run manually so not Read Only mode. HOW??? It says enter root password for maintenence or ctrl-D to continue (which reboots) this is really stupid as my password doesnt work (i guess it is because there is no root!). Its like the old classic "Keyboard error press a key to continue"! Why cant it ask for LOGIN name and password?

How can i run it manually if i cannot even get to a shell?

---

### Post by dgrafix on 2009-08-21
HMM in my anger i have found a real hacky way round it.

Ctrl+alt+f2 to get another session and then ctrl-alt-delete.
X attempts to load, fails and drops to a login.

Real smooth! :rolleyes:

:lolflag:

Perhaps i could suggest a **proper shell login** for that "password for maintenence shell or (ctrlD to continue)" message?

---

### Post by matthewbpt on 2009-08-21
I suggest booting a live cd and fsck the partition from the live cd. This should be able to fix any errors then you can boot normally again.

---

