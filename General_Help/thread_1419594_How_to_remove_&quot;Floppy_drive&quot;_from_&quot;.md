---
title: "How to remove &quot;Floppy drive&quot; from &quot;Places&quot; menu?"
date: 2010-03-02
forum: General Help
---

### Post by pstein on 2010-03-02
By default my "Places " menu contains some entries like
 
- Floppy menu
- Desktop
- Computer
 
How can I get (permanently) rid of these entries ? 
 
How can I rename "Home Folder" to "Home" ?
 
Peter

---

### Post by Rhubarb on 2010-03-02
The places menu contents comes from a hidden file in your home directory.

To modify this file just open up a terminal, and run the following:-

```
gedit ~/.gtk-bookmarks
```

There you may delete the entries you do not wish to see, then save the file.

If the changes don't come into effect immediately, try logging out then back in again.

---

### Post by pstein on 2010-03-02
This is not true as you can see from the attached snapshot:
 
[http://img442.imageshack.us/img442/7885/capture20100302084000.png](http://img442.imageshack.us/img442/7885/capture20100302084000.png)
 
Where is the "Documents" entry from the bookmark file?
 
Where is the corresponding "Computer" entry from "Places" in the Bookmark file?
 
Peter

---

### Post by Rhubarb on 2010-03-02
Ok, sorry about that, I thought you were referring to the bookmarks in the Places menu.

Looking at your screenshot there, it looks as though you're running vmware workstation.
If you wish to remove the floppy drive, you could disable emulation of a floppy drive in vmware.

As for configuring the rest, I'm really not sure.
A brief Internet search didn't come up with anything relevant.

You could try opening up nautilus, and right clicking on the relevant entries you wish to modify in the Places part (see attached). - But I haven't got this working on my machine (Ubuntu 10.04 alpha 3).

---

### Post by Mr.BS on 2013-02-13
Use the 'Archive Manager' to delete unwanted entries in Places.

---

### Post by slickymaster on 2013-02-13
At a terminal window, run the following command:
```
sudo geany /etc/fstab
```
_Note:_ Replace geany with your installed texpad.

Fill in your password and press 'Enter'. This will open the fstab and you have to search for the line that starts with ```
/dev/fd0
``` and place an **#** at the beginning of that line to disable the floppy drive. After that, save and close your fstab file.

Finally run the following command at the terminal window:
```
sudo modprobe -r floppy
```

That's it, the floppy drive is disabled and will no longer be listed in your Places Menu.

---

### Post by oldos2er on 2013-02-13
Old thread closed.

---

