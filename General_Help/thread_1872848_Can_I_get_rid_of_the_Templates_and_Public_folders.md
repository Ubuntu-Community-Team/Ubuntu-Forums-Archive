---
title: "Can I get rid of the Templates and Public folders?"
date: 2011-10-31
forum: General Help
---

### Post by tpprynn on 2011-10-31
I've manually deleted these as I have never needed them, but of course they reappear next boot. I imagine there is something I can delete elsewhere to stop them reappearing?

Thanks.

---

### Post by hwttdz on 2011-10-31
You can check ~/.config/user-dirs.dirs and comment out the lines corresponding to the folders you don't want, and then remove the folders.  That said I'm not terribly familiar with KDE so I'm not so sure.

---

### Post by tpprynn on 2011-10-31
Thanks.

I think I may have been stuck with them because I had Xubuntu and Ubuntu before on this netbook - maybe Kubuntu doesn't have these folders. I did a better job of getting rid of old folders in /home and the Projects and Templates folders haven't come back for a boot or two, must be sorted.

Useful bit of knowledge from you there though for my other Gnomeified computer.

---

### Post by mcduck on 2011-10-31
You can also easily hide such folders, which is a god idea if you might actually want to use some templates at some point but still don't want to see the folders every time you open your home directory.

Just create a file called ".hidden" in the same place where you want to hide something, and then add every file and folder you wish to hide to that file, on on each line. Most graphical file browsers respect this method and hide the defined items, although they will still appear in command-line.

---

### Post by hwttdz on 2011-10-31
Awesome:
```
Last edited by tpprynn; 1 Hour Ago at 02:55 PM.. Reason: Doubts about the spelling of the made-up word 'Gnomeified' 
```

---

