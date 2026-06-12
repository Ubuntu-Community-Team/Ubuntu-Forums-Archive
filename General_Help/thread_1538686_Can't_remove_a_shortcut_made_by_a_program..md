---
title: "Can't remove a shortcut made by a program."
date: 2010-07-25
forum: General Help
---

### Post by xBiocorex on 2010-07-25
Hello there, I'm a bit of a noob when it comes to Ubuntu. I recently installed Acetone ISO in the hopes of installing a program, but alas it doesn't do what I need it to (run the MDF file like a disk rather than showing all the files in it, and because this is a multi-disk thing I'm installing I'm kinda stuck now) and I noticed it would make a new virtual drive every time I mounted an image, and I wound up with four of them, and each one had its own shortcut on my desktop. Well, I removed the program and deleted the folder it created, but these shortcuts are still on my desktop. And they are UNTOUCHABLE! 

The command line ls -al ~/Desktop/ will show everything on the desktop BUT THEM, they have no permissions, and cannot be moved, copied, or deleted, because Ubuntu can't find volume information on them. I reinstalled the program to see if anything would help, and I noticed that the drives would go away if I unmounted the image (I coulda sworn I told it to before, but it didn't want to...) but now these drives are errors to the program, and I still can't remove the shortcuts.

---

### Post by limestone on 2010-07-25
try in terminal
```
sudo rm -r foldername
```
or sudo rm filename

---

### Post by borth92 on 2010-07-25
> **pont.andersson said:**
> try in terminal
```
sudo rm -r foldername
```or sudo rm filename

this guy is giving good advice, since the program probably just made the shortcuts in root.
you could also type this into the terminal:
gksudo nautilus

this will open up the file browser as root.

---

### Post by xBiocorex on 2010-08-08
Oh god, I forgot about this topic, sorry. ><

I never wound up using that, they kind of removed themselves after a while. I think reinstalling the program and then just rebooting the computer is what fixed it.

---

