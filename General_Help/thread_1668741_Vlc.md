---
title: "Vlc"
date: 2011-01-16
forum: General Help
---

### Post by Bolshy on 2011-01-16
[I][SIZE=3][FONT=Lucida Console]Hi I have a problem with my vlc player it all installed ok and plays music/videos ok but it also opens everything else on my computer, for example I try to open My Documents and it comes up with VLC Player same goes with Pictures home folder etc etc does anybody know why and how to resolve the problem.
Thanks in advance.
[/FONT][/SIZE][/I]

---

### Post by mc4man on 2011-01-16
Find a folder, any folder and right click -> 'open with - other application'
From the list pick 'Open Folder', then click open

That will reset the default folder handler back to nautilus

In the future whenever using the 'open with other application' menu make sure to uncheck the 'Remember this application...' option or the default will be changed to the app chosen.

(Leave ck.'ed when setting the default back to nautilus

---

### Post by can2002 on 2011-01-16
[FONT="Verdana"][SIZE="3"]Look in ~/.local/share/applications for a file called mimeapps.list, you should see something like:

[Added Associations]
inode/directory=FILENAME

If you've not intentionally custom commands to open directories, you can delete the whole line (starting inode/directory) and also the filenames referenced by the line (in the same directory as mimeapps.list - usually starting userapp-???????).

If that does it, you've previously tried to open a directory with VLC and accidentally checked the box saying 'Remember this application for "folder" files'.

Cheers,
Chris[/SIZE][/FONT]

---

### Post by Bolshy on 2011-01-16
> **mc4man said:**
> Find a folder, any folder and right click -> 'open with - other application'
From the list pick 'Open Folder', then click open

That will reset the default folder handler back to nautilus

In the future whenever using the 'open with other application' menu make sure to uncheck the 'Remember this application...' option or the default will be changed to the app chosen.

(Leave ck.'ed when setting the default back to nautilus
  Well thanks - I did what you said and touch wood all is well many many thanks :D

---

### Post by apsot on 2011-01-24
> **can2002 said:**
> [FONT="Verdana"][SIZE="3"]Look in ~/.local/share/applications for a file called mimeapps.list, you should see something like:

[Added Associations]
inode/directory=FILENAME

If you've not intentionally custom commands to open directories, you can delete the whole line (starting inode/directory) and also the filenames referenced by the line (in the same directory as mimeapps.list - usually starting userapp-???????).

If that does it, you've previously tried to open a directory with VLC and accidentally checked the box saying 'Remember this application for "folder" files'.

Cheers,
Chris[/SIZE][/FONT]

[SIZE="4"]that was really helpful. Many thx can. My problem appeared when opening a directory from chromium or deluge. Now all solved.[/SIZE]

---

