---
title: "Can't find /google-earth/uninstall"
date: 2009-09-06
forum: General Help
---

### Post by toleolu on 2009-09-06
Trying to install Google Earth (Ubuntu 9.0.4) and kept getting those errors on start up about not being able to create a cache directory, etc.

Anyway, I tried one of the fixes I saw posted about installing the .bin as root, or as sudo, something like that. 

I want to completely remove google earth and try again, but I can't find the /google-earth directory. I found a /.googleearth and deleted that, but I still have an icon under Internet Applications for Google Earth. It crashes, so I want to remove it and try again.

Thanks

---

### Post by Barafu Albino Cheetah on 2009-09-06
You don;t understand how packaging works. Menu launcher was created by system scripts embedded into installer you started. Uninstaller may remove it, but nothing MUST do it, so remaining menu entry means nothing except that you'll have to remove it manually. 
Install google-earth from google repository. Works really great.

P.S.  By the way, you can run "sudo updatedb", and after that use "locate myfile" to search for files.

---

### Post by toleolu on 2009-09-06
Whether I install Google Earth through Synaptic or by the .bin from Google I get the same errors when it starts. That's what I have been trying to fix, I keep getting the errors about not being able to create the cache dir or access to a couple of other files, it's a permissions thing.

Anyway, I found /google-earth in /opt and remove it there. Now I will try to re-install and fix the permissions thing.

Thanks

---

