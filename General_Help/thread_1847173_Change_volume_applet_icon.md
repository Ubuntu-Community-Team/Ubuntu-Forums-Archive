---
title: "Change volume applet icon"
date: 2011-09-20
forum: General Help
---

### Post by editheraven on 2011-09-20
I have unistalled pulse audio server/driver and left only alsa sound driver by following this guide : [http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/](http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/) . But when i run the script volbar.py the icon for volume control applet is different (like this : [http://img801.imageshack.us/img801/4898/screenshotrg.png](http://img801.imageshack.us/img801/4898/screenshotrg.png) ). Where from can i change that icon?

---

### Post by Frogs Hair on 2011-09-20
Location of the icon depends on how you install your Icons . Icon sets installed by default or for all users are in the file system - usr/share/icons . Gksu nautilus will be command needed to make changes in this folder.  

Icon sets installed for your own use from other sources can be found in home/hidden Folders in .icons . Which folder the panel icons are located in may vary from set to set . You need to rename or replace and rename if you want a different icon.

Something that seems simple can be a little work due to the variation in icon sets . Good Luck !

---

