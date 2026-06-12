---
title: "Missing My Documents Folder"
date: 2009-12-31
forum: General Help
---

### Post by shinji00 on 2009-12-31
Yesterday, I downloaded one application but accidentally placed it to *My Documents* folder instead of C://. After I removed the application, I found out that *My Documents* folder was removed too. The *Document*s folder under the *"Places" *isn't there anymore. I tried to restart my laptop (cos I was hoping that when I come back, the folder will be there), but unfortunately, nothing happened. 

What should I do? I tried to create another *Documents *folder but I can't find Document config in the emblem -and the newly created "fake Document folder" doesn't come out in the "places" drop down list. :( Please help me.

---

### Post by shairozan on 2009-12-31
Hey, the easiest way to fix this will be to just put the new "fake" documents folder in the places list. You can add any folder on your system that you can access to the places folder. 

To do this, you'll want to access it via the file browser (Either got to places computer, places home, etc). Once this open, navigate to the folder you want to add. 

Once you're in the folder you want to add, click on the "Bookmarks" section of the toolbar at the top. Click "Add Bookmark". Then it will be visible in the "places" toolbar.

---

### Post by shinji00 on 2009-12-31
How about the emblem config of that fake folder? and it doesn't have correct icon too.

---

### Post by Seq on 2009-12-31
Hi, what you want to do is edit the file that lists the special XDG directories.
```
.config/user-dirs.dirs
```

If you run gedit (or the text editor of your choice) you can open that file. If you're not familiar with unix file naming, the prepended period hides the directory, so you won't actually see it. Just type it in to the open dialog and it will work.

In that file is a mapping of XDG directories and their associated actual location. When your Documents directory (or any other XDG directory) gets removed, they fall back to your home. There is no way to repoint it without editing this file.

You may need to log out and back in.

---

### Post by shinji00 on 2009-12-31
>  Hey, the easiest way to fix this will be to just put the new "fake" documents folder in the places list. You can add any folder on your system that you can access to the places folder. 

To do this, you'll want to access it via the file browser (Either got to places computer, places home, etc). Once this open, navigate to the folder you want to add. 

Once you're in the folder you want to add, click on the "Bookmarks" section of the toolbar at the top. Click "Add Bookmark". Then it will be visible in the "places" toolbar.

Thanks! I got that one! But how can I restore the original *document* icon?

---

### Post by shinji00 on 2009-12-31
> **Seq said:**
> Hi, what you want to do is edit the file that lists the special XDG directories.
```
.config/user-dirs.dirs
```If you run gedit (or the text editor of your choice) you can open that file. If you're not familiar with unix file naming, the prepended period hides the directory, so you won't actually see it. Just type it in to the open dialog and it will work.

In that file is a mapping of XDG directories and their associated actual location. When your Documents directory (or any other XDG directory) gets removed, they fall back to your home. There is no way to repoint it without editing this file.

You may need to log out and back in.

How can I do that? In terminal? I really have no idea what you're talking about since I just installed this Ubuntu yesterday. However, If I do that, will the default *Document* icon be restored?

---

### Post by Seq on 2009-12-31
> **shinji00 said:**
> How can I do that? In terminal? I really have no idea what you're talking about since I just installed this Ubuntu yesterday. However, If I do that, will the default *Document* icon be restored?

Yes.

From my earlier message:
> If you run gedit (or the text editor of your choice) you can open that file. If you're not familiar with unix file naming, the prepended period hides the directory, so you won't actually see it. Just type it in to the open dialog and it will work.

gedit can be launched by clicking the Applications menu, going to Accessories, and selecting gedit. You can open a file by selecting "File" and "Open". In this dialog you can type ".config/user-dirs.dirs" and click open.

You will want to change the line for XDG_DOCUMENTS_DIR to reflect your new Documents directory. If you called it "Documents", then you would change that line to look like this:
```
XDG_DOCUMENTS_DIR="$HOME/Documents"
```

---

### Post by shinji00 on 2009-12-31
Oooooops! I lost you in this part:

> You can open a file by selecting "File" and "Open". In this dialog you can type ".config/user-dirs.dirs" and click open.I think there's no way to type in that code in this dialogue box..

[IMG]http://i392.photobucket.com/albums/pp6/imaleya/Screenshot.jpg[/IMG]


EDIT:
Oh! and yeah! I also tried to type the code in search (in this dialogue box), but nothing happened.

---

### Post by Seq on 2009-12-31
> **shinji00 said:**
> Oooooops! I lost you in this part:



I think there's no way to type in that code in this dialogue box..

[IMG]http://i392.photobucket.com/albums/pp6/imaleya/Screenshot.jpg[/IMG]

Whoops ;)

Click that pencil in the top-left corner. The text field you need to type in is hidden by default. After clicking the pencil, the text field will appear.

Also, that setting is saved for next time you open files. Since it was visible for me, I neglected to mention it. Sorry.

---

### Post by Seq on 2009-12-31
Also some handy Gnome file-management shortcuts.

CTRL+L shows and hides that box. It does the same thing in the regular file manager.

CTRL+H shows hidden files and folders (like the .config folder we're looking for). It does this in the file manager as well. This setting is remembered, and it clutters up your dialog with dozens of directories you don't need to see typically, which is why I didn't suggest it initially.

---

### Post by shinji00 on 2009-12-31
AAAAAHHHHH!!! THANK YOU SOOOOOOOO MUCH!! You're my savior! Happy New Year to you! :)

---

