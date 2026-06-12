---
title: "editing folder shortcuts on right sidebar"
date: 2009-08-26
forum: General Help
---

### Post by Arkitekt on 2009-08-26
I recently purchased a HP Mini 110 - 1030, I have dual-booted it with W7 RC and UNR (updated and fixed sound issue). I have set each O/S partition to 20GB which leaves just over 100GB remaining. I partitioned it and formatted it as NTFS in W7, and then installed ntfs-config in UNR and set it for automount. 

This large partition has been labeled Media and will serve as a shared Media partition for both O/S's. 

My question is this: on the right sidebar in UNR there are folder shortcuts for Documents/Music/Pictures/Videos. How do I change it so that those shortcuts open up the folders of the same name on my Media partition and not in the UNR partition.. also is it possible to add to that sidebar? possible a Ebook folder?

---

### Post by Arkitekt on 2009-08-26
anyone?

---

### Post by P4man on 2009-08-26
I do not know the UNR. But in nautilus (filemanager) you can make "favourites" as easy as dragging a folder and dropping it on the left pane under "places". These places also show up in the gnome "paces" menu, so if the UNR interface gets its folders from there, then its dead easy.

If that doesnt work, then I read a while ago you can reassign the locations of your Documents, Pictures etc folders by editing a config file somewhere. I dont have it at hand, but if need be, I can hunt it down for you (unless someone can post it ?)

---

### Post by Arkitekt on 2009-08-26
Thanks, that helped me figure it out, now just have to figure out how to change the default save location for Cheese Webcam Booth, or find a better webcam program

---

### Post by P4man on 2009-08-26
Heh.. that made me find the "other" solution. From cheese faq:

> Where does cheese store my photos?

Depending on your settings, they are stored in the XDG-directories for photos and videos

Thats what i had in mind as second way. You can edit xdg directories with:

```
gksudo gedit /etc/xdg/user-dirs.defaults
```

However, it says there: "the values are relative pathnames from the home directory".. so i guess you'll have to make a link in your homedirectory if you want to refer to a folder outside your homefolder. And now you'll ask me how, and I'll blush and say:

 Im not sure..

something with "ln".. someone else pls help ? :)

---

### Post by felixq78 on 2011-05-22
We forget so easily how difficult it was when we first started on Linux. Newbies need step by step instructions omitting nothing. Telling someone to "open a terminal" means SFA to a newbie.
We gotta remember that otherwise they'll give up and go back to Windo$e

---

