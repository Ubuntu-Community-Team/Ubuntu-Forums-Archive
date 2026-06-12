---
title: "File associations and icons not showing on desktop"
date: 2011-06-29
forum: General Help
---

### Post by arvsr1988 on 2011-06-29
For the past few days my file associations have gone for a toss. For example : 
[LIST]
[*]an icon on the desktop to open eclipse says eclipse.desktop and doesn't show the eclipse image 
[*]when i right click a .bz2 file it doesn't show the extract here option
[*]for text files, a small bit of the text is showing outside the icon where it usually shows inside
[/LIST]

The same problems are present in nautilus as well as the desktop. 

Need some quick help to reset these to the default. 

Have attached a screenshot to show the issue.

---

### Post by arvsr1988 on 2011-06-29
ok so i googled a bit and installed rox-filer - that has fixed some of the associations but not all of them ... here's the output i get when i ran sudo apt-get install rox-filer

> 
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for man-db ...
Setting up rox-filer (1:2.5-1build1) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'


---

### Post by ajgreeny on 2011-06-29
Are all those icons I see files you have on your desktop, and not icons to start applications?

If you right click on, for example, timesheet.xls and go to properties, how is it set to open in the "Open with" tab, and similarly for all the other file types?

Occasionally I have seen the error messages you show in terminal when installing applications, and I read somewhere that it might be solved by re-installing the following packages:
**gnome-mime-data**
**shared-mime-info**
which seemed to fix that error message problem, but whether it will fix the display problem you have I can't say;  worth trying, I think.

---

### Post by arvsr1988 on 2011-06-29
tried sudo apt-get install gnome-mime-data and sudo apt-get install shared-mime-info in terminal - get an output that they are already the newest version.

---

### Post by ajgreeny on 2011-06-29
Try ```
sudo apt-get install --reinstall gnome-mime-data shared-mime-info
```

---

### Post by arvsr1988 on 2011-06-29
getting the following error after trying the reinstall command 

> 
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'


---

### Post by arvsr1988 on 2011-06-29
i rebooted my system a while after doing the reinstall - now things seem to be working fine.

---

### Post by ajgreeny on 2011-06-29
Yes, sorry.  I forgot to mention the reboot being needed.

By the way, I think the original problem arises sometimes after installing packages that are not in the standard ubuntu repos, perhaps from a ppa or another source.  I have no idea why, but that "re-installing" trick has worked for me a few times.

---

