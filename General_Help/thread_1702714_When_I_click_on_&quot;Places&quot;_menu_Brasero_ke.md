---
title: "When I click on &quot;Places&quot; menu Brasero keeps launching, can't view files!"
date: 2011-03-08
forum: General Help
---

### Post by oxf on 2011-03-08
Yesterday I burnt a couple of CD's with Brasero. Project completed sucessfully.

But.. now if I try and open Nautilus and go to any of my folders under Places>Home/Music/Documents, in fact anywhere, it goes straight into Brasero and seems to think I have an uncompleted project. 

There is also a box open which promts me to rename/not rename for full Windows or Linux comaptabilty. As of right now I cant get rid of Brasero and get to any folders/files.

Anyone have sugestions please??
Thanks

---

### Post by oxf on 2011-03-08
The other weird thing is this. When Brasero pops up there's the folder containing the tracks I burnt to CD yesterday displayed. I try to delete it and Brasero shuts down.
Still doesn't mean I can access my files browser though!

Help anyone????:confused:

---

### Post by oxf on 2011-03-08
Any ideas folks? AS it stands right now I can't access any files via the PLACES menu.

I don't think the problem is inherently linkd to Brasero, I suppose it could be any other application that taken "control" of the menu.

Thanks

---

### Post by oxf on 2011-03-09
Help! Does anyone have any sugestions as to what's going on?

For what it's worth if I open Nautils via the terminal with root privaliges I can browse my files. But not if I click on Places on the tool bar. That just opens up Brasero every time.
I have no idea what happened to cause this!

---

### Post by QLee on 2011-03-09
> **oxf said:**
> ..
But.. now if I try and open Nautilus and go to any of my folders under Places>Home/Music/Documents, in fact anywhere, it goes straight into Brasero and seems to think I have an uncompleted project. 
...
Anyone have sugestions please??
Thanks

This might be worth trying.

When you access "Computer" from the Places menu does it open correctly?

If so, when you have accessed (clicked on) "Computer" from the top panel, you are looking at a file browser window which shows whatever partitions are on your hard disk (shown as drive icons), a cdrom if you have one and "Filesystem" (also shown as a drive icon), is that correct?

If so. right click on the "Filesystem", and select "Properties" from the context menu (should be down at the bottom). After the properties sheet opens, select the "Open With" tab to see what the system thinks it should do. (Note: That Open With tab on the properties sheet has a reset button) You'll probably want to reset to "Open Folder".

---

### Post by grahammechanical on 2011-03-09
I think that you have somehow changed the Open with preference.

I suggest that you right click the desktop and select create folder. then you right click the new untitled folder and select Open with Other application and from the list you select File Browser.

Then the system will associate the Nautilus file browser with your instruction to open the Places folder and every folder.

Regards.

---

### Post by oxf on 2011-03-09
Thank you so much, that fixed it! I don't know how this happened but yes it had been switched to open Brasero instaead of folder.

Thanks
Katja

---

