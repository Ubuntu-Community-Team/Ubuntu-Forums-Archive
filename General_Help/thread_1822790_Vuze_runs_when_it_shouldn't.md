---
title: "Vuze runs when it shouldn't"
date: 2011-08-11
forum: General Help
---

### Post by bluesummer on 2011-08-11
Hi forum. First time posting; just started using Ubuntu and i love it. I downloaded 11.04 and have been getting the hang of it, but i could use some help. 
 
I click the icon on the left side menu to open the Files and Folders tab, then i get to choose which folder to open (Documents, Pictures, Videos, etc..); here in is the problem. It doesn't matter which folder i choose, they won't open; instead Vuze starts to run. I can't for the life of me understand why or how to change this. 
 
Any help would be greatly appreciated.

---

### Post by sikander3786 on 2011-08-11
Go to Terminal under Applications > Accessories sub-menu in classic Gnome or press the <Super> key and search the Dash for 'Terminal' in Unity. Type:

```
nautilus
```

Now right-click any folder you see and go to 'Open with other application'. Choose 'File browser' in the following dialog and tick the box for 'Remember this application for 'folder' files' just near the bottom.

---

### Post by bluesummer on 2011-08-11
There is no check box at the bottom of that window.

---

### Post by sikander3786 on 2011-08-11
Please take a look at the screenshots below.

[ATTACH]199815[/ATTACH]

[ATTACH]199816[/ATTACH]

**Added:** You need to choose 'File Browser' which isn't highlighted in the 2nd screenshot. I was lazy :D

---

### Post by bluesummer on 2011-08-11
I did as you said, but in the "open with" window there is no box to tick or sentence that says "Remember this application for "folder" files". There is nothing between >Use a custom command  and the Remove, Cancel, or Open buttons.
 
Also, i noticed that it is any of the shortcuts under the Files and Folders tab that open Vuze. Whether its a file or folder in the Recent File, Download, or Favorites Folder list.

---

### Post by sikander3786 on 2011-08-11
That is strange. Can you please post a screenshot? You can find a screenshot utility by searching the Dash in Unity or under Applications > Accessories > Take Screenshot.

---

### Post by bluesummer on 2011-08-11
Update:
 
So its only when i try to open anything in the Files and Folders tab in the unity launcher that vuze opens. I uninstalled Vuse to see what the association would be without it and i get an error now when i try to open anything in the Files and Folders tab. 
 
I get "Failed to execute default File Manager: Failed to execute child process "/usr/bin/vuze" (No such file or directory)
 
I think i made it mad.
 
Also, i'm using a second computer to post online at the moment because i don't have internet through my laptop at work. So i can't post a screenshot. But i promise you its just like the picture you posted ubt without that line. There isn't even a gap where it should be.

---

### Post by bluesummer on 2011-08-11
Update part 2!:
 
It's not just the links in the Files and Folders tab in the Unity launcher that are opening vuze. I have an external hdd that mounts in the Unity launch bar and it also opens vuze as well as the trash can at the very bottom of the unity launcher. 
 
I can open all of these normally through all other means, its just when i use the unity launcher that they are associated with Vuze.

---

### Post by bluesummer on 2011-08-11
YAY!!! I finally found someone with a similar issue. They deleted a few things i didn't have installed, but they one that i did have seemed to be the culprit.

I went into ubuntu software center > installed software > and removed "Utility files for libexo" and bam! problem solved!!

Thanks sikander3786 for everything!

---

