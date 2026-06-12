---
title: "How to change permissions on files so I can copy them freely"
date: 2011-04-30
forum: General Help
---

### Post by Daanii on 2011-04-30
My laptop has Ubuntu as a dual boot. Many times I want to copy files from one folder to another. But I run into permissions problems. 

For example, I downloaded a program that required me to put a rules file in /etc/udev/rules.d  But when I tried to do that, I got an error: "permission denied"

Is there any way to change permissions on folders so that I can freely copy them from one folder to another? That would make life a lot easier.

---

### Post by dylbud on 2011-04-30
I would recommend the following. Go to one of your desktop panels, right click, and choose "add to panel". In the menu that comes up, click the first option: "custom application launcher". Then, another window comes up. Choose "application" from the drop down list, then choose a name for your launcher, like "browse as root" for example. 

Then for command, type "gksudo nautilus". This will open Nautilus (the file browser, like windows explorer), but it will open it as root, with full permissions. So then you close that box and a new launcher button appears on the panel. Click it. Before it opens Nautilus, it will bring up a dialog box that you have to enter your password into. Then you just go for it, moving and deleting files like crazy!!

(I'll assume I don't have to tell you not to delete or move any files that could screw up your system)

---

### Post by wgarcia on 2011-04-30
From the command line you can prepend "sudo" to commands to overcome permissions problems.

Or "Alt-F2" enter "gksudo nautilus" and then you get a file browser where you are running as superuser and can move files around freely. 

But be careful because you can really destroy your system using these commands if you erase/move/overwrite the wrong files/folders.

---

