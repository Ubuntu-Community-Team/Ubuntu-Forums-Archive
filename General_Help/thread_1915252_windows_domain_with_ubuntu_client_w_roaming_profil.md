---
title: "windows domain with ubuntu client w/ roaming profile?"
date: 2012-01-25
forum: General Help
---

### Post by wwarsin on 2012-01-25
Is it possible to have a ubuntu client connect to a windows domain and login with roaming profiles enabled? Preferably something that is somewhat compatible with switching between windows desktop and ubuntu.

I tried doing a search and can only find ubuntu servers and roaming profiles, but not ubuntu client with roaming profile.

Thanks

---

### Post by dcstar on 2012-01-25
> **wwarsin said:**
> Is it possible to have a ubuntu client connect to a windows domain and login with roaming profiles enabled? Preferably something that is somewhat compatible with switching between windows desktop and ubuntu.

I tried doing a search and can only find ubuntu servers and roaming profiles, but not ubuntu client with roaming profile.


"Roaming Profiles" are Windows specific things, they do not apply to Linux.

---

### Post by whaase on 2012-01-25
Several years ago we had XP stations with roaming profiles on a SuSE server. It would stand to reason it should be able to be done with Linux clients? It's in samba.. I just can't remember how we did it.

---

### Post by wwarsin on 2012-01-26
Ah, okay maybe i could create a logon script for ubuntu that would map the specific folder from the "roaming profile" to the folder in ubuntu...

---

### Post by dcstar on 2012-01-27
> **wwarsin said:**
> Ah, okay maybe i could create a logon script for ubuntu that would map the specific folder from the "roaming profile" to the folder in ubuntu...

People have used NFS shares to achieve this sort of thing:

[https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

