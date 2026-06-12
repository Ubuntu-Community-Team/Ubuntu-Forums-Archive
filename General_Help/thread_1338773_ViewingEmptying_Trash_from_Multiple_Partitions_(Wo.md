---
title: "Viewing/Emptying Trash from Multiple Partitions (Workaround)"
date: 2009-11-26
forum: General Help
---

### Post by acoc on 2009-11-26
I currently have a three partition setup for ubuntu, /, /boot, and /mnt.  Mnt is where I put a vast majority of my data (ie photos, documents, music, etc) so if I ever put a clean install of a distro, this data never gets touched and I can link to it within my /home/user directory.  So based on the trash specification ([http://www.ramendik.ru/docs/trashspec.html](http://www.ramendik.ru/docs/trashspec.html)) set down by the freedesktop.org overlords, each partition must have it's own .Trash folder and keep everything deleted from that partition in that location.  From what I understand, the reason is for windows compatibility and to prevent having to write the data to another partition to add it to one big trash folder.  

The problem is that the trash applet only looks in the /home/user/.local/share/Trash folder, so it's not able to handle trash from multiple partitions.  Therefore, I created this ugly little workaround which suits my needs and may be of use to someone else.  I first created the folder ~/.trash-dirs and linked to the files directory of each of the partition's trash folders.

```
mkdir ~/.trash-dirs
cd ~/.trash-dirs
ln -s ~/.local/share/Trash/files home_trash
ln -s /mnt/.Trash/1000/files mnt_trash
```

Then I created a simple little script to erase the contents of these directories.

```
nano emptytrash.sh

#!/bin/bash
rm -rf ./home_trash/*
rm -rf ./mnt_trash/*
```

NOTE: It is never a good idea to blindly create or execute scripts that someone on a forum suggests.  You should always read and understand what it does before executing it and if you don't, ask someone else to evaluate it for you.  This goes doubly so for anything with a "rm -rf" command or anything run as a superuser.

Set the permission to execute.

```
chmod u+x emptytrash.sh
```

To allow easy access to this directory I first removed the old trash applet (right click, remove from panel) and right clicked on the panel and "add to panel".  I created a custom application launcher with the name Trash Dirs, the command nautilus ".trash-dirs" and selected a trash icon I picked up on the internet.

To view or empty my trash I now just click on this icon and can see either one of my trash folders and can double click on emptytrash.sh to clean them out.

John

---

