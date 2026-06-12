---
title: "default file drag to different drive"
date: 2011-05-20
forum: General Help
---

### Post by munky99999 on 2011-05-20
Gnome Ubuntu

I mounted a drive on my desktop as a folder. When I drag and drop a file on the folder it makes a copy. This is the correct default behaviour.

I would like to change this behaviour such that it moves the file to the drive and doesnt leave a file behind.

I am more then aware of the Mouse3 menu drag possibility but I am trying to change the default behaviour instead. So I dont have to act like it's different then a folder; thusly less clicks.

Anyone know how I might do this?

---

### Post by linuxinstalledfromhdd on 2011-05-20
you would need to write a bash script file that copies the file to that device and then removes the residual file you selected to copy.  Make the script file executable with chmod 775 and move it into a common path directory.  Essentially creating a custom command line command to do exactly what you want to have done each time you invoke it.

---

### Post by munky99999 on 2011-05-20
> **linuxinstalledfromhdd said:**
> you would need to write a bash script file that copies the file to that device and then removes the residual file you selected to copy.  Make the script file executable with chmod 775 and move it into a common path directory.  Essentially creating a custom command line command to do exactly what you want to have done each time you invoke it.
How does a bash script help in dragging and dropping? If I were doing this at the cli I could just do 'mv file folder/' and there's no issue.

---

### Post by linuxinstalledfromhdd on 2011-05-20
that requires an extra step though..  It sounds like they want it done in just one command. A bash file can be invoked in one command from it's common path directory to do everything they want in one step. That way they don't have to think about it, or explain the routine of what files to rm to some other user too.

---

### Post by munky99999 on 2011-05-20
> **linuxinstalledfromhdd said:**
> that requires an extra step though..  It sounds like they want it done in just one command. A bash file can be invoked in one command from it's common path directory to do everything they want in one step. That way they don't have to think about it, or explain the routine of what files to rm to some other user too.

Im not doing any of this at the commandline. So I'm fairly sure a bashscript isnt going to help here.

---

### Post by dcstar on 2011-05-20
> **munky99999 said:**
> Gnome Ubuntu

I mounted a drive on my desktop as a folder. When I drag and drop a file on the folder it makes a copy. This is the correct default behaviour.
.........

"Dragging" will **move** files/folders on the **same** filesystem. Between **different** filesystems it will **copy**.

---

### Post by munky99999 on 2011-05-20
> **dcstar said:**
> "Dragging" will **move** files/folders on the **same** filesystem. Between **different** filesystems it will **copy**.

Indeed as I said in first post. How do I change this behaviour?

---

### Post by dcstar on 2011-05-20
> **munky99999 said:**
> Indeed as I said in first post. How do I change this behaviour?

You don't. It is designed to do precisely that and nothing else in the default Ubuntu file manager - I don't know if other alternative file managers do things differently.

PS - You can apparently use the Shift key to force a Move:

[http://developer.gnome.org/hig-book/stable/input-mouse.html.en#drag-drop-override](http://developer.gnome.org/hig-book/stable/input-mouse.html.en#drag-drop-override)

---

### Post by linuxinstalledfromhdd on 2011-05-20
Just write a bash script file to do what you want to do. Command line rocks.

---

### Post by munky99999 on 2011-05-20
> **dcstar said:**
> You don't. It is designed to do precisely that and nothing else in the default Ubuntu file manager - I don't know if other alternative file managers do things differently.

PS - You can apparently use the Shift key to force a Move:

[http://developer.gnome.org/hig-book/stable/input-mouse.html.en#drag-drop-override](http://developer.gnome.org/hig-book/stable/input-mouse.html.en#drag-drop-override)

Yes or use mouse3 to drag then you get options.

Nautilus only recently changed to become like every other manager. I simply want an option to change the behaviour. Why is it so hard?

---

