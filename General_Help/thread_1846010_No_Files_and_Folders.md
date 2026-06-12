---
title: "No Files and Folders"
date: 2011-09-18
forum: General Help
---

### Post by Noob2011 on 2011-09-18
Hey strange problem. I cannot access " the files and folders" section.  i get this message. Please help if you can. Thanks

---

### Post by Krytarik on 2011-09-18
Try this, making sure the package "gvfs-bin" is installed:
```
sudo apt-get install --reinstall gvfs-bin
```
Then relogin.

Hope it works!

---

### Post by Noob2011 on 2011-09-18
Thanks mate. I will check it out... 

cheers

---

### Post by Noob2011 on 2011-09-18
Hi.. It reinstalled but did not work. I am still not able to browse the directories. I created a new user and there it worked just fine. So its with the main user login its messed. 

Thanks

---

### Post by Krytarik on 2011-09-18
Try adding the below line to the "[Added Associations]" section of your  "~/.local/share/applications/mimeapps.list", to look like this:
```
[Added Associations]
inode/directory=nautilus-folder-handler.desktop;
```

---

### Post by Noob2011 on 2011-09-18
Hi.. I managed to open the  file via gedit and this was in it.

--------------------------------------------------
[Added Associations]
application/vnd.ms-access=openoffice.org-base.desktop;
audio/x-mpegurl=vlc.desktop;totem.desktop;brasero.desktop;qmmp.desktop;rhythmbox.desktop;qmmp_enqueue.desktop;gedit.desktop;wine-extension-txt.desktop;openoffice.org-writer.desktop;
application/x-ms-dos-executable=wine.desktop;
video/x-ms-wmv=totem.desktop;vlc.desktop;qmmp_enqueue.desktop;
application/xspf+xml=totem.desktop;firefox.desktop;wine-extension-xml.desktop;gedit.desktop;wine-extension-txt.desktop;openoffice.org-writer.desktop;vlc.desktop;


[Removed Associations]
inode/directory=nautilus-folder-handler.desktop;
-----------------------------------------------------

I added the assoiciation and removed the entry under  [Removed Associations] .. 

I will reboot and message back in about 5 mins... 

Thanks

---

### Post by Noob2011 on 2011-09-18
Thank you Krytarik... It works... :popcorn:):P Thank you very much for your help. 

Best regards

dc

---

### Post by Krytarik on 2011-09-18
Great! :D

Noted the [Removed Associations] thing for future queries, didn't take this into account till now, though I remember having noticed those section before. Thanks, too!

---

### Post by Noob2011 on 2011-09-18
Cheers. ):P

---

