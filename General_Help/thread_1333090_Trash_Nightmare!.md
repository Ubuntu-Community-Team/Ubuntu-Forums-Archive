---
title: "Trash Nightmare!"
date: 2009-11-21
forum: General Help
---

### Post by neilevan814 on 2009-11-21
Ok..I have just reinstalled to a whole new OS (Karmic Koala) to try and get rid of this trash issue from Jaunty, but it is still there.

I have three items in trash trash:/// 
permissions are owner root group neil
I checked ~/.local/share for Trash and it does not exist
from the desktop trash icon if I click empty trash I get a pop up window saying file operations preparing andd then it just bleeps away and the trash is still there...

Help!

I found the culprit in a separately mounted hard drive 
did a sudo rm -rf .Trash-1000/files/*

---

