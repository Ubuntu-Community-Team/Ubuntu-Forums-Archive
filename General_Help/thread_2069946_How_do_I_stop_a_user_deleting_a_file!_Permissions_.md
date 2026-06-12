---
title: "How do I stop a user deleting a file?! Permissions not working for me."
date: 2012-10-11
forum: General Help
---

### Post by QwUo173Hy on 2012-10-11
I'm setting up an Ubuntu box for my nephew. I've made one account where I want the wallpaper to not be deletable.

I did:
```
sudo chown root wallpaper.png
sudo chgrp root wallpaper.png
sudo chmod -w wallpaper.png
```
The icon now has the padlock emblem on it, but guess what? You can right click and send to trash! You can also empty the trash and the file is gone altogether.

I'd like to know:
How come making it a root file doesn't make the file annoyingly persistent like I believe it did in the past?
How can I make this file unremovable *without* making root own it? This is important because LightDM can't preview it when I do that.

Many thanks Ubuntu brigade,
Ten

---

### Post by drmrgd on 2012-10-11
I think you have to change the permissions of the folder containing the file in this case and not the file itself.  When you delete a file, you're actually writing in the directory and not writing to the file itself.  Try changing the ownership and permissions of the directory that contains the picture to see if you can delete it.

---

### Post by Carborundum on 2012-10-11
> **drmrgd said:**
> I think you have to change the permissions of the folder containing the file in this case and not the file itself.  When you delete a file, you're actually writing in the directory and not writing to the file itself.  Try changing the ownership and permissions of the directory that contains the picture to see if you can delete it.
This is correct. Alternatively, you can use chattr to flag the file as immutable:
```
sudo chattr +i wallpaper.png
```This will prevent everyone (even root) from removing the file (of course, root can just make it mutable again with chattr -i).

---

### Post by Morbius1 on 2012-10-11
The rwx of a file determines if a given user can can write ( and by extension - delete ) the contents of that file.

The rwx of the directory does exactly the same thing to the contents of the directory. Write permissions to a given user allows him to delete the contents of that directory - in this case a file. 

To prevent a user from having the ability to delete a file you must remove write permissions to the parent folder by that user. Something like this:
```
sudo chmod 0755 /path/to/parent/folder
```If this is a common directory where anyone can add files then you can use the "sticky bit" which allows a user to delete his own files only. Something like this:
```
sudo chmod 1777 /path/to/parent/folder
```

---

### Post by QwUo173Hy on 2012-10-12
drmrgd, Carborundum, Morbius1 - thank you for collaboratively and incrementally explaining it. It's like you rehearsed it :)

So does this mean that the "contents" of the file and the outer "husk" of the file are treated separately? I've read up on linux permissions but it was mostly the same and lists of commands without much background info.

---

### Post by Vaphell on 2012-10-12
you can say that. File modification (content of the file changes) is exactly that, file modification, but file creation/removal is modification of the dir (content of the dir changes).

---

