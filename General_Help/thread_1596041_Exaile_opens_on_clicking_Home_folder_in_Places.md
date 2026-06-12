---
title: "Exaile opens on clicking Home folder in Places"
date: 2010-10-13
forum: General Help
---

### Post by ksourabh on 2010-10-13
Hi,
I am having this odd problem since I did a clean install of Maverick. I installed Exaile music player but after that when I click on 'Home folder' (or any subfolder in it) under 'Places' menu Exaile pops up instead.
I uninstalled exaile for a while and everything worked fine but reinstalling it caused the same problem again.

Any help........

Thanks in Advance

---

### Post by mc4man on 2010-10-13
This is a bug in ubuntu that has been somewhat ignored. to return nautilus as the default folder handler r. click on any folder (if none available on Desktop then just create one) -> Open With -> Other Application
scroll down and choose 'Open Folder'

This is caused by using the Open With -> Other Application on a folder - whatever app chosen will become the new default folder handler.

Choices available in the Open With menu will not be set as default so you should be good as far as exaile from now on

(if you uncheck the remember box then choice will not be set as default

---

### Post by ksourabh on 2010-10-13
thanks for quick reply, that worked :)

---

### Post by userFrodo on 2010-10-18
Thanks for the reply and post.

I had the same problem, except that the folder was opened using Xine.

All is fine now.

---

