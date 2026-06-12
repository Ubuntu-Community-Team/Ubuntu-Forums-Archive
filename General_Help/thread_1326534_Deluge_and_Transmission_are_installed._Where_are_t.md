---
title: "Deluge and Transmission are installed. Where are they?"
date: 2009-11-14
forum: General Help
---

### Post by brjoon1021 on 2009-11-14
I have 2 bittorrent clients installed. But Miro TV application always tries to open torrent files. I uninstalled Miro. No love. I still don't have any option to open with either of my bt applications.

It looks like I have to use the "open with" option, but I don't see those apps in directory that is opened automatically by the system. So, where would I find these apps or how would I select one of these to be default?

b

---

### Post by toammann on 2009-11-14
You can provide the path to an executable in the open with dialog. To find that one just type ```
locate transmission
``` in the Terminal. If that doesn't yield results retry again, after first typing ```
sudo updatedb
```.

---

### Post by imtheguru on 2009-11-14
Assuming you're using Ubuntu.

Right click on a .torrent file.
Properties > Open With > Transmission.

.torrent files are now associated with Transmission.
Double click on .torrent file.

Cheers.

---

### Post by ed-koala on 2009-11-14
If Deluge doesn't appear as an option in the open with program choices, you can manually find it under /usr/bin.  I had to go there and choose Deluge to associate my torrents with it, everything is fine now.  Just be sure to check the always use this app box and you only gotta do it once.

---

