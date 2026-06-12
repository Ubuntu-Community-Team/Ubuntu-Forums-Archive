---
title: "I don't know where my deleted files go"
date: 2010-06-08
forum: General Help
---

### Post by paparozoumis on 2010-06-08
After I delete them, I open the bin and it's empty. 
Do they get deleted permanently at once or what?
If there's an option like that, I want to disable it as it's extremely easy to delete a file and at least you have a second chance to get it back if it's done by mistake...

ANyone?

---

### Post by mkvnmtr on 2010-06-08
As I understand it when you delete a file it is not moved. Only the address of that file is deleted and the space of the file is free to be used again. Until it is used the file is still there you just have to use special software to find it.

---

### Post by efflandt on 2010-06-08
If you "Move to Trash" in the file browser, it puts it in your trash (wastebasket like icon at bottom of screen, usually), which is actually in ~/.local/share/Trash (the dot prefix on .local in your home directory makes that hidden in file browser unless you press Ctrl+H).

If you **rm** a file or **rm -r** directory from a terminal or console, consider it gone for good, without using some sort of file recovery tools quickly.  If you reboot it may get overwritten.  So be VERY careful about using wildcards (*).  It is best to **ls** your filespec before **rm**, so you know what you will be deleting.

---

### Post by unperson on 2010-06-08
How are you deleting the files?  By default, if you select a file (with the left mouse button) in the Nautilus file browser and press the delete key, the item should be moved to the trash bin.  If you press the right mouse button it should bring up a menu (the context menu) that may give you the choices "Move to trash" and "Delete".  The former will move the file to the trash bin, obviously, but the latter will simply delete the file for good.  You can get rid of the delete option in the context menu as follows: Open the file browser, from the menus at the top select Edit->Preferences, select the Behavior tab, and unselect the check box that includes the delete command.  If you delete files from the terminal using the 'rm' command, again they are simply deleted, not moved to the trash.

The last poster talked about retrieving deleted files.  It is true in most file systems that when you delete a file it simply "unlinks" th file, removing the information that points to the file's contents rather than doing anything do the contents themselves.  That data will hang around for a while until the space is needed and it is overwritten by different data.  However, "undeleting" files (as it is sometimes called) is a tedious process, and you can't count on the data being intact.  This is something that should not be relied on and should only be resorted to a case where you've accidentally lost important data.

Hope that helps.

---

### Post by paparozoumis on 2010-06-10
> **efflandt said:**
> If you "Move to Trash" in the file browser, it puts it in your trash (wastebasket like icon at bottom of screen, usually), which is actually in ~/.local/share/Trash (the dot prefix on .local in your home directory makes that hidden in file browser unless you press Ctrl+H).

If you **rm** a file or **rm -r** directory from a terminal or console, consider it gone for good, without using some sort of file recovery tools quickly.  If you reboot it may get overwritten.  So be VERY careful about using wildcards (*).  It is best to **ls** your filespec before **rm**, so you know what you will be deleting.


OK.. let's take it from the start to make things more clear..

First of all, when I said "delete", I meant using the right mouse button or  choosing the files and hitting the Del key and moving the files to the Trash bin, not using any 'crazy' rm commands from within the terminal.

The problem was that by using these two methods, the moved files should be in the trash bin waiting to be permanently deleted or moved back to their original places. 
Instead, my trash bin was EMPTY and the moved files were not there!!!!



> **unperson said:**
> How are you deleting the files?  By default, if you select a file (with the left mouse button) in the Nautilus file browser and press the delete key, the item should be moved to the trash bin.  If you press the right mouse button it should bring up a menu (the context menu) that may give you the choices "Move to trash" and "Delete".  The former will move the file to the trash bin, obviously, but the latter will simply delete the file for good.  You can get rid of the delete option in the context menu as follows: Open the file browser, from the menus at the top select Edit->Preferences, select the Behavior tab, and unselect the check box that includes the delete command.  If you delete files from the terminal using the 'rm' command, again they are simply deleted, not moved to the trash.

The last poster talked about retrieving deleted files.  It is true in most file systems that when you delete a file it simply "unlinks" th file, removing the information that points to the file's contents rather than doing anything do the contents themselves.  That data will hang around for a while until the space is needed and it is overwritten by different data.  However, "undeleting" files (as it is sometimes called) is a tedious process, and you can't count on the data being intact.  This is something that should not be relied on and should only be resorted to a case where you've accidentally lost important data.

Hope that helps.

After I posted my initial message, I searched a bit and found that in my /home/user folder, there was no .trash folder . I created one and the moved to trash files were finally able to be found again after being moved to the trash bin. 

Also, in the Behavior tab, the box referring to the delete commmand was unchecked. 

Another thing is that in ~/.local/share/Trash -mentioned by efflandt- there were a few files laying there..

The question is: Where EXACTLY is the trash bin located in Ubuntu|?
Is it ~/.local/share/Trash or /home/user/.trash ? ? ? ?

---

### Post by kennedyvelez on 2010-06-10
> **paparozoumis said:**
> After I delete them, I open the bin and it's empty. 
Do they get deleted permanently at once or what?
If there's an option like that, I want to disable it as it's extremely easy to delete a file and at least you have a second chance to get it back if it's done by mistake...

ANyone?



Sir,
 testdisk or photorec via synaptic or download foremost _[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)_

---

### Post by plucky on 2010-06-10
> The question is: Where EXACTLY is the trash bin located in Ubuntu|?

Read [This](http://ubuntuforums.org/showthread.php?t=898573&highlight=drs305)

Good Luck

---

### Post by philinux on 2010-06-10
> **paparozoumis said:**
> 
The question is: Where EXACTLY is the trash bin located in Ubuntu|?


 ~/.local/share/Trash and if you delete stuff while using sudo or gksudo nautilus you get some here /root/.local/share/Trash

---

### Post by neednewlaptop on 2010-06-10
Did you ever log out the user you are using. I noticed that the bin only displays items when the user has logged out an then back in, after this first log out it usually works fine. I don't know if you perhaps created the user, logged in and just stayed logged in.

---

