---
title: "File permissions in a shared area for media files"
date: 2009-09-19
forum: General Help
---

### Post by fatphilthethird on 2009-09-19
Hi

Two people use my PC and all our photos, mp3 etc are in a shared area we can both access.

The problem is when I add to this area, by importing with picasa or using ripperx for example, the end files have permissions based on whomever did the creation.

I would like the files to automatically be available to both users. Could someone point me in the right direction? I could set up a third dummy user account with both real users able to access their files and use this account to create media or I could retrospectively chown or chgrp but I suspect there's an easier way.

Any ideas appreciated

Thanks

Phil

---

### Post by blueridgedog on 2009-09-19
You need to set the file creation mask for your files (the umask).  See:

[http://osr507doc.sco.com/en/OSTut/Setting_your_file_creation_mask.html](http://osr507doc.sco.com/en/OSTut/Setting_your_file_creation_mask.html)

---

