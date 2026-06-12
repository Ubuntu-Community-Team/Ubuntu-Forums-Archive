---
title: "removed home icon in firefox whcih file is affected"
date: 2009-07-03
forum: General Help
---

### Post by b-boy on 2009-07-03
Hi 


I removed the home icon in firefox and I would like to know which file does it change as i want to user that file on other computers so that i dont have to do each one

---

### Post by ajgreeny on 2009-07-03
> **b-boy said:**
> Hi 


I removed the home icon in firefox and I would like to know which file does it change as i want to user that file on other computers so that i dont have to do each one
If you mean the home icon in the FF toolbar, you can get it back by right clicking in the toolbar and choosing "Customise"  You can then drag the icon back to the toolbar.  If this is not what you meant by your problem, can you explain in a bit more detail what exactly you want.

---

### Post by b-boy on 2009-07-03
> **ajgreeny said:**
> If you mean the home icon in the FF toolbar, you can get it back by right clicking in the toolbar and choosing "Customise"  You can then drag the icon back to the toolbar.  If this is not what you meant by your problem, can you explain in a bit more detail what exactly you want.

no this is not what i need.


The home icon has been removed so I would like to transfer this browser without the home icon to several other PCs but i cannot do them on at a time as there are many so I would like to know what file says the home icon must not be displayed e.g prefs.js so that i can copy this file to all the PCs and all of them wont have the home icon

---

### Post by komputes on 2009-07-03
You are trying to take a firefox profile and copy/multiply it on all the computers you manage. Go to your home directory and press CTRL-H to view hidden files. Take ~/.mozilla from the computer and copy it to a FAT32/16 USB disk, go to the second computer and drop it in the home directory of the user.

I say FAT32/16 because this strips away owner/permission. If you copy onto ext2/3/4 or tar compress it first it will retain permissions, in which case, after copying to the second computer you will have to run:

```
chmod -R theusername:theusername ~/.mozilla
```-or-

```
chmod -R UUID:UUID ~/.mozilla
```So for example my username is komputes and my UID:GID is 1005, I would run
```

chmod -R komputes:komputes ~/mozilla
```-or-

```
chmod -R 1005:1005 ~/mozilla
```If all these computers are on the same network and have been ser up for file sharing via samba, nfs, ssh/scp there may also be other ways to do the transfer.

---

