---
title: "New folder button in Nautilus"
date: 2010-09-22
forum: General Help
---

### Post by mschira on 2010-09-22
Hi Folks, 
I am mighty annoyed that I have to dive into the file menue to create a new folder.
So I googled and found something that supposedly fixes it.:

[http://ubuntugenius.wordpress.com/2010/05/13/add-buttons-for-new-folder-cut-copy-paste-delete-to-the-nautilus-toolbar/](http://ubuntugenius.wordpress.com/2010/05/13/add-buttons-for-new-folder-cut-copy-paste-delete-to-the-nautilus-toolbar/)

So I tried that, for starters I only added the line 

<toolitem name="Cut" action="Cut"/>

and saved nautilus-navigation-window-ui.xml again.
However this has NOOO effect.
:confused:
What am I doing wrong?
M.

---

### Post by mschira on 2010-09-23
solved it. There was one Nautilus still running, the one showing the desctop. So I had to do a killall nautilus.
Now it works,
:guitar:

---

