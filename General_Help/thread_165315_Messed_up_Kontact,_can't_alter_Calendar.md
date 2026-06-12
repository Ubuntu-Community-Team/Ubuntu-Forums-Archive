---
title: "Messed up Kontact, can't alter Calendar"
date: 2006-04-24
forum: General Help
---

### Post by Gijith on 2006-04-24
Hello,

I posted this in the KDE PIM mailing list, but figured I'd take a shot here too. 

I did something very stupid. I've recently changed from kubuntu 5.10 to 6.06. And in the process, I've made a real mess out of the Kontact suite through my own mistakes. When I upgraded, I did a fresh install. And concerned about losing some of my addressbook info, I wanted to back things up. A received some apparently poor advise to simply backup what files were in ~/.kde/share/apps/kabc. So I did this, adding these files into the same directory in Dapper. When I started Kontact, everything was good (old contacts intact), except that I couldn't make any changes to the Calendar. I get "Error while saving default Korganizer resource" message when attempting to do anything.

In desperation, I made what was probably another poor newbie decision and uninstalled and reinstalled Kontact from Adept. I did this in the naive hope that it would somehow fix the problem (it didn't). This turned into a mess, as reinstalling involved many more packages, than uninstalling (though I think I've got them all now).

I'd be very very grateful if anyone can offer advise on how to fix this problem with KOrganizer. Sorry I can't provide a more detailed description of this error I'm getting, but I wouldn't know where to look...

Thank you very much.

PS: I think these are all the packages I reinstalled. Did I miss any? kontact, libkpimidentities1, libkdepim1a, kdepid-kresources, kdepim-kio-plugins, kamil, akregator, kaddressbook, korganizer, knotes, knode, kpilot, kandy, kitchensync

---

### Post by darkarchon on 2006-04-24
well, maybe u need to change the owner of that ~/.kde/share/apps/kabc dir. i never used that prog myself, but give it a try :)

---

### Post by Gijith on 2006-04-24
[QUOTE=darkarchon]well, maybe u need to change the owner of that ~/.kde/share/apps/kabc dir. i never used that prog myself, but give it a try :)[/QUOTE]

Thanks for the suggestion, but ownership is already in my name.

Any other ideas? :-k

---

### Post by Gijith on 2006-04-26
Bump.

Any ideas? I'd love to get this working.

---

### Post by frahi on 2006-05-07
One idea would be to export the contacts. Delete the directory (of course backup it) and restart kaddressbook (or kontact). Then it should (I'm not sure) recreate the directory and it's one empty database. Afterwards you can import your data again. 
A big disadvantage of this idea is that you cannot be sure to have all data again, because the export and import may not convert 1:1. So please check the import contacts. 

If you tried this, please report about success/failure here.

---

