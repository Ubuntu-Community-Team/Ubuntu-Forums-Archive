---
title: "updated azureus and now it wont work"
date: 2006-03-03
forum: General Help
---

### Post by risknothin on 2006-03-03
So azureus told me to update and i did and now it wont open, i even uninstalled azureus and reinstalled it with automatix and it still wont start.  Any ideas?

---

### Post by prizrak on 2006-03-03
How are you starting it? When I used it I just made a shortcut to run azureus.jar, maybe you just need to update your shortcut?

---

### Post by sbassett on 2006-03-03
[QUOTE=prizrak]How are you starting it? When I used it I just made a shortcut to run azureus.jar, maybe you just need to update your shortcut?[/QUOTE]


Also, if this is still not starting at all, I would consider getting rid of your config directory. I believe it is either .Azureus or .azureus.

---

### Post by risknothin on 2006-03-03
i cant figure out how to pinpoint .azureus directory to be removed.  any suggestions?

---

### Post by bored2k on 2006-03-03
In your file browser, VIew --> Show hidden files OR hit Ctrl+H and delete it.

---

### Post by risknothin on 2006-03-03
worked!!! thanks, the problem is that it asks me to update a library and that screws it up so i just dont download that and it works.

---

### Post by theToolman on 2006-03-07
Yip I had same problem: updated and azureus died.  looks like (for me at least) I had a .Azureus folder and it created a .azureus folder.  if you remove and resinstall via apt/automatix and remove both .azureus and .Azureus it starts fine.  

remember this is likely where your torrent history and current ones are stored - you might want to go in to these folders and surgically removed the offending update chunk.

---

### Post by nalgene on 2006-03-07
okay its true it when you update hte last swt gtk update.  Is there a fix to this? is the swt gtk needed?

---

