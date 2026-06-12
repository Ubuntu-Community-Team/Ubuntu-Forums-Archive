---
title: "how to install icon package from a folder"
date: 2011-08-05
forum: General Help
---

### Post by jolian ramos on 2011-08-05
how to install icon package from a folder 

&
this is the link to the icon package folder i want to add them to my ubuntu 10.04

[http://gnome-look.org/content/show.php?content=28754&forumpage=1](http://gnome-look.org/content/show.php?content=28754&forumpage=1)

---

### Post by bodhi.zazen on 2011-08-05
copy the icon folder to ~/.icons

---

### Post by Frogs Hair on 2011-08-05
You may need to extract the zip file by right clicking the package and selecting extract here first . Open the folder because there two packages within .

---

### Post by 3Miro on 2011-08-05
Extract the archive and it should have a folder inside containing the subfolders 36x36 48x48 and so on. You have to move the folder either to /home/your_username/.icons (use Ctr+H to show hidden folders and you can create the folder is it doesn't already exist). Or you can move the folder to /usr/share/icons, however, you will need to start the file manager with
```
gksudo nautilus
```
so you can write to the system folder. Note that writing to system folders can mess things up so you should be careful.

PS. Another way is to just open System -> Prefs -> Appearance and drag/drop the archive into the Appearance window.

---

### Post by jolian ramos on 2011-08-05
> **3Miro said:**
> Extract the archive and it should have a folder inside containing the subfolders 36x36 48x48 and so on. You have to move the folder either to /home/your_username/.icons (use Ctr+H to show hidden folders and you can create the folder is it doesn't already exist). Or you can move the folder to /usr/share/icons, however, you will need to start the file manager with
```
gksudo nautilus
```so you can write to the system folder. Note that writing to system folders can mess things up so you should be careful.

PS. Another way is to just open System -> Prefs -> Appearance and drag/drop the archive into the Appearance window.
[SIZE=3] Thank you all for your trial to help me, but please, what do you mean that i need to write in system file  ,and what should i write inside it exactly ?[/SIZE]

---

### Post by 3Miro on 2011-08-05
> **jolian ramos said:**
> [SIZE=3] Thank you all for your trial to help me, but please, what do you mean that i need to write in system file  ,and what should i write inside it exactly ?[/SIZE]

Anything outside of /home belongs to the system and you should be very careful when you make any changes to the files and folders. Putting the icon folder in /usr/share/icons is fine, but if you accidentally do something else (like delete configuration files in /etc/), it can completely break your system.

---

