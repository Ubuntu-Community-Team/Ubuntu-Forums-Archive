---
title: "How to move all contents inside a windows folder link"
date: 2012-08-31
forum: General Help
---

### Post by funkdified on 2012-08-31
My windows install on my dual boot has been corrupted... I need to backup certain files. I am currently trying with Nautilus and Dolphin to make a backup of "My Documents" and a few other folders. My documents is a "link" and when I copy it in ubuntu I merely get a link pointing to the other partition. How can I copy the actual contents of a linked folder, as well as the contents of any linked folders contained within? (recursive linked directories)

---

### Post by Paddy Landau on 2012-08-31
Mount your Windows drive and browse your files from there. You can do that in Nautilus. That way, you will be copying the files instead of a link to your Windows document folder.

---

### Post by funkdified on 2012-08-31
> **Paddy Landau said:**
> Mount your Windows drive and browse your files from there. You can do that in Nautilus. That way, you will be copying the files instead of a link to your Windows document folder.

Thanks for you response. This is exactly what I am trying to do, but the links are copying (through Nautilus and Dolphin), not the folder and it's contents.

---

### Post by Paddy Landau on 2012-09-01
I'm confused. You said, 'My documents is a "link"'. That indicates that you are not copying the files but instead copying a link to the files.

[LIST]
[*]If you open Nautilus, you should see your Windows drive in the left-hand pane at the top under the heading *Devices*.
[*]Click on it to auto-mount the drive and take you there.
[*]In the right-hand panel, go to Users > [your name].
[*]Press Ctrl+2 to view the details; you will then see each folder listed as either a "folder" or a "Link to folder".
[*]Copy only the ones marked "folder". E.g., copy "Documents" and not "My Documents". Also be sure to look inside the folders, as you may find links within "Documents".
[/LIST]

---

