---
title: "File transfering Permissions"
date: 2010-01-28
forum: General Help
---

### Post by nesone on 2010-01-28
I have a usb harddrive with info im trying to copy on to my local HD with ubuntu running. Some of the files transfered fine besides these mac libery file when i try to drag and drop into a folder on the desk top it says I cant handle this file because i do not have permissions. Is there away to take control of the permissions on this folder and its contents? Sorry I have only had ubunto for about a year so I'm still learning. Thanks in advance for any advise!

---

### Post by The Men on 2010-01-28
Check the file permissions.

```
cd /media/<device>/ && ls -al | grep <file>
```

---

### Post by nesone on 2010-01-28
> **The Men said:**
> Check the file permissions.
 
```
cd /media/<device>/ && ls -al | grep <file>
```
 
 
Sorry Im not sure what how to do that can you be more specific?

---

### Post by john_spiral on 2010-01-28
looks like the copy command 'cp' might be the business:

[http://www.edugeek.net/forums/mac/18043-how-do-you-copy-folder-preserve-ownership-permissions-2.html](http://www.edugeek.net/forums/mac/18043-how-do-you-copy-folder-preserve-ownership-permissions-2.html)

---

### Post by blueshiftoverwatch on 2010-01-28
> **nesone said:**
> Is there away to take control of the permissions on this folder and its contents?
If you want to change the permissions of a file/folder from the GUI you can:

1. Enter **gksudo nautilus** into the terminal
2. Right click on a file/folder -> properties -> permissions
3. Change the owner to your username and select "create and delete files"
4. Change file access to "read and write"
5. Click "apply enclosed permissions to enclosed files"

---

