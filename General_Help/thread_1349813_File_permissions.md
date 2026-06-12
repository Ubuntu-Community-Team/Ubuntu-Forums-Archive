---
title: "File permissions"
date: 2009-12-08
forum: General Help
---

### Post by BobSongs on 2009-12-08
I've looked at various file permission tutorials. They've helped to a certain degree. But I'm looking for some guidance as to how to set this up the best way. I don't know how to create groups, apply groups to a folder, or add users to a group in the terminal.

**[SIZE="3"][COLOR="DimGray"]situation[/COLOR][/SIZE]**
640 GB HDD cut into 4 partitions:

[LIST]
[*]22 GB /dev/sda1 for **/**
[*].9 GB /dev/sda2 for **swap**
[*]164 GB /dev/sda3 for **/sharedfiles**
[*]453 GB /dev/sda4 for **/home**
[/LIST]
The issue is with **/sharedfiles** and setting its permissions, etc. True: I could go into it and hammer a solid```
sudo chmod 777 /sharedfiles
```and be done with it. But this seems to be a bit too brute force.

[LIST]
[*]I want to create a group (**sharedusers**)
[*]I want the **sharedusers** group to have power to create files/folders
[*]I don't want anyone outside that group to have power over the folder, not even to list its files.
[*]I want to be able to do these things from the command prompt without the assistance of the GUI.
[/LIST]

**[SIZE="3"][COLOR="DimGray"]history[/COLOR][/SIZE]**
I have messed up this folder a bit with some testing of what I've read over at Linux File Permissions tutorial sites, particularly with the -R switch on chmod. As soon as I used the -R the folders within have become unrecognised, particularly the **lost&found** folder.

A well-written tutorial covering this would be appreciated if you don't wish to write out how this would be done.

---

### Post by firsttimeuser on 2009-12-08
groupadd shareedusers
chgrp sharedusers /sharedfiles
chmod g+rwx /sharedfiles
chmod o-rwx /sharedfiles

---

### Post by BobSongs on 2009-12-08
*nods in appreciation to **firsttimeuser***

---

