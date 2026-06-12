---
title: "deleting all files of gdesklets?"
date: 2006-05-30
forum: General Help
---

### Post by closeyourwindows on 2006-05-30
so I have been deleting gdesklets and I want ALL of it removed, so I did sudo apt-get remove --purge gdesklets and that did not remove all instances of the program, I still have 54 files left over, I searched for them in the GUI and selected all of them but access denied.  Is there a way to use the terminal to search for all the files, and delete them?

I did try locate gdesklets and I can see all the files, however I have to delete them one by one, and what I want to do is delete all of them at once using sudo.

---

### Post by aysiu on 2006-05-30
```
sudo updatedb
locate gdesklet
``` For how to remove files you don't have permissions to: [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

