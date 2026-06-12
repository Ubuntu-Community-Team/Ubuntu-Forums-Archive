---
title: "Please Help! cant boot up, need to salvage pics and documents"
date: 2010-04-11
forum: General Help
---

### Post by 93jam on 2010-04-11
Hi, I have ubuntu 9.10, and Im not sure what happened, but I cant boot, Im fine with doing a reinstall, and I know how, but my main concern in getting my pics back, I hav a few folders I havent had a chance to back up. When I boot from a 9.10 live cd, I can find the HD and my home folder, but some individual pics it said I dont have premission to move, so is there another live cd, or a way to bypass that? anyone who could help would be a lifesaver, thanks!

---

### Post by jflaker on 2010-04-11
> **93jam said:**
> Hi, I have ubuntu 9.10, and Im not sure what happened, but I cant boot, Im fine with doing a reinstall, and I know how, but my main concern in getting my pics back, I hav a few folders I havent had a chance to back up. When I boot from a 9.10 live cd, I can find the HD and my home folder, but some individual pics it said I dont have premission to move, so is there another live cd, or a way to bypass that? anyone who could help would be a lifesaver, thanks!

live CD....

in terminal
```
 gksudo nautilus 
```


You SHOULD be able to move data....move to a FAT32 USB drive so the files lose the security and ownership info and you can again access it from a new account if you reload..

---

### Post by 93jam on 2010-04-15
Thanks! With your help I was able to move them to safety! Does anyone know if there is a way to get to my bookmarks in firefox?

---

### Post by House101 on 2010-04-15
Are you running a nvidia driver and does the screen go black after bootind and just keep churning? Because if it does, I had the same problem, it has to do with the lack of support, I'd need to see my computer to tell you what to do, but if that is what you have, it's solvable!! :)

---

### Post by 93jam on 2010-04-15
no, I dont have nvidia, it is a intel integrated graphics card.

---

### Post by gadolinio on 2010-04-15
> **93jam said:**
> Thanks! With your help I was able to move them to safety! Does anyone know if there is a way to get to my bookmarks in firefox?

See if you have this folder:
/home/USERNAME/.mozilla/firefox/SOMETHING.default/bookmarkbackups
You might well back up the entire .mozilla folder from your user's directory, and then paste it in the new installation.

---

