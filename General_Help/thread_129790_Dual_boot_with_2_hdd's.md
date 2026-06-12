---
title: "Dual boot with 2 hdd's"
date: 2006-02-14
forum: General Help
---

### Post by angelcosta on 2006-02-14
First, i installed winxp on my second hd (hdb or hd1), then installed ubuntu on the main one, which didnt detect windows already installed.
How do i get my winxp running again? I tried editting menu.lst and now it looks like this:
```
title		Windows 95/98/NT/2000
rootnoverify		(hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader	+1
boot (not sure about this one)
```

now i get an error saying "missing ntldr". what can i do?

---

### Post by Robgould on 2006-02-14
you need to repair your master boot record. Run fixmbr from the rescue mode on your windows install cd. This will get you booting back to windows. You will then have to use the ubuntu disk to re-install grub.  There may be an easier way, but I don't know it.

---

