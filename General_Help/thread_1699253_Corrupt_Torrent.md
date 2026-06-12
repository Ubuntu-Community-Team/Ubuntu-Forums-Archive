---
title: "Corrupt Torrent"
date: 2011-03-03
forum: General Help
---

### Post by eipapp on 2011-03-03
HELP  !!!!

Don't know what the correlation is, if any, but just added a printer to my computer but when I went to print a document to make sure it was working properly I got the following message when I clicked on "Places" ; "Documents; 
"Couldn't add corrupt torrent".  
This also happened when I tried to open my pictures folder.
I did go into my expansion drive, retrieved a document and printed it so I know printer is working fine but why can't I open my documents folder ???

Regards,
Bruce

---

### Post by WorMzy on 2011-03-03
Sounds like you've (possibly accidentally) told Ubuntu to associate folders with a torrent program.

To fix it, first press Alt+F2, then run this:
```
gedit .local/share/applications/mimeapps.list
```

In the opened file, press Ctrl+F and search for
```
inode/directory
```

Once found, delete this line, save the file, then close gedit.

---

### Post by drpjkurian on 2011-03-03
It seems to be related to torrent files and the transmission. How come it is related to opening the folder??

---

### Post by Verbeck on 2011-03-03
> **drpjkurian said:**
> It seems to be related to torrent files and the transmission. How come it is related to opening the folder??
'cause its a file association issue, directories are bieng opened by transmission

---

### Post by eipapp on 2011-03-03
Just to make sure I'm doing the right thing......
I followed your instructions and is this the line I'm to delete in entirety: (including the words inode/directory or just what follows the word directory) ?

inode/directory=transmission.desktop;file-roller.desktop;

---

### Post by Verbeck on 2011-03-03
the entire line including 'inode/directory'

---

### Post by WorMzy on 2011-03-03
Yep, delete the entire line.

What that is telling Ubuntu is that you want to open directories with transmission by default, and if that's not available, to use file-roller instead. Neither of these applications should even be associated with this mime type, so deleting the entire line will make Ubuntu use the system default (which is nautilus) instead of your personal defaults.

---

### Post by eipapp on 2011-03-03
Worked just like you said.
Thanks so much, everyone, for all your help.

Bruce

---

### Post by omnom on 2011-03-04
thanx a lot!!!!!! **_PROBLEM SOLVED_** :popcorn:

---

