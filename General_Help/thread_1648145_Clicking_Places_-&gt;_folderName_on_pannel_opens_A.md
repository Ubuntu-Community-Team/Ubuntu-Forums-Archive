---
title: "Clicking Places -&gt; folderName on pannel opens Archive manager instead of file manage"
date: 2010-12-18
forum: General Help
---

### Post by Dave001 on 2010-12-18
Somehow the default action for opening a place got changed to archive manager.
This specific problem leads to a larger question about getting rid of" [x] always open with this application" inadvertent selections and how to make them go away.

---

### Post by Dave001 on 2010-12-22
Got the answer on Launchpad about 15 min after I posted. Here's how you do it:

In ~/.local/share/applications/mimeapps.list I found:
 [Added Associations]
inode/directory=file-roller.desktop;nautilus-folder-handler.desktop;gedit.desktop;thunderbird.desktop;
 and changed it to:
 [Added Associations]
inode/directory=nautilus-folder-handler.desktop;gedit.desktop;thunderbird.desktop;
 Logged out/in. Problem solved.

---

### Post by parsh78 on 2011-01-09
Thanks, this fixed it. Another ways is to right click on a folder and in Open With Application select File Browser.

---

