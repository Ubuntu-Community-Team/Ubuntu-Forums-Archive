---
title: "How do you delete an Icon under the places drop down menu?"
date: 2009-09-12
forum: General Help
---

### Post by concerto on 2009-09-12
I don't know how I did this but if you look at the top of the screen you will see 3 pull down menus.  Applications, Places, and System.

Well under the Places tab I have managed to get random short cut folders in there and I cant delete them.  I deleted the main files and now when I click on the folder I get an error message.

How do I add and delete folders in this tab?

Sorry for such a weird question but it's driving me crazy.

thanks

---

### Post by jerrrys on 2009-09-12
have you tried **gksudo nautilus**

---

### Post by CatKiller on 2009-09-12
> **concerto said:**
> How do I add and delete folders in this tab?

It's not that clear from your post, but I think you're talking about Bookmarks. Open a Nautilus and select Edit Bookmarks from the Bookmarks menu entry, and you should be able to remove them.

---

### Post by Efwis on 2009-09-12
He is talkubg about the folder in the places menu on gnome-panel. I don't know of a way to remove the shortcuts but you can hide them.

```
sudo apt-get install menu-editor
```

or if you prefer use synaptics to install it. it will be shown in Applications>other
click on that and you will be able to change what icons are shown in the menus.

---

### Post by corncob on 2009-09-12
When you open the drop down menu under PLACES click on something that you don't want to delete like your home folder.  A window opens up showing the icons for the files in your home folder on your right with the menu list in a column on the left.  You can delete items from there.  Right click on it and then select "Remove".  If you want to add something to the list, say a file from your home folder while you have it open, just drag it over with your mouse.

---

### Post by sigmarhophi on 2009-09-12
Ok, I am writing this post not in ubuntu so most of what I am going to say is from memory.  I have had the same issues, random items showing up under places, and the links would never go away.  The solution is not an easy right click or press delete, but still pretty straight foward.  all the "links" for the gnome-panel and "places" are stored in an xml file under your users directory.  so: /home/*user*/.gnome/ 
-do a search through the files looking for the key word of the name of the link you want to go away.  I suggest searching only because I do not remember the name of the file.
-edit the xml file using your favorite editor.
-remove the call to the item by deleting the line.
-save the file. 
-refresh or restart gnome-panel.

---

### Post by concerto on 2009-09-12
ok.  It looks like the icon in the places menu was a bookmark after all.  I kept opening up nautilus and it kept saying that I didn't have any bookmarks.  well... I didn't have any under ROOT but I did some how accidentally make them under my user name.

I could not have solved this issue if it wasn't for the help everyone here gave me.  I can't thank you enough.

You guys are awesome!!!!!!!!

---

### Post by steveneddy on 2009-09-14
Open your /home folder

Go to "Bookmarks"

add/delete menu items there

---

