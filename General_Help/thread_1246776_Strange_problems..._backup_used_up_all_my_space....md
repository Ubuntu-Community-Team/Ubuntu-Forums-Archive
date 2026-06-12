---
title: "Strange problems... backup used up all my space..."
date: 2009-08-22
forum: General Help
---

### Post by roffle on 2009-08-22
Hi guys, I recently switched from OSX to Ubuntu and its all been going smooth so far except one thing...

Firstly, I installed sBackup and configured it to backup my home folder onto my External firewire drive. This seemed to work ok until I disconnect my drive later on (I didnt notice the checkbox to abort backups if the destination doesnt exist in sBackup config) and noticed it must've kept backing up when I woke up in the morning and all the disk space was gone (currently 0 bytes free) . Then i noticed in '/media' i have '/media/My Book' and '/media/My Book_' the former being something left there for some reason and the latter is what my firewire drive has now become. Strange thing is when I look in Disk Usage Analyser it doesnt show where all tmy disk space has gone...

Then i rebooted and i noticed my WLAN wouldnt connect, firefoxs' bookmarks were gone, my bookmarked directories etc. from Nautilus and the Places menu gone etc. Like as if my preferences or some config file or something is missing...

Anyone have any clues why this is happening and how I can fix it?

---

### Post by P4man on 2009-08-22
if your root is full, weird things can happen. Perhaps thats why its not loading your ff profile. Id suggest booting off a live cd, mounting the drive and having a good look what happened. It does seem like sbackup made the /media/My Book folder when you disconnected the actual drive and then ate your diskspace.

---

### Post by roffle on 2009-08-22
Thanks for the reply. Boot off a live cd and look at what? How could I delete that folder '/media/My Book'? It doesnt have an unmount option or delete from nautilus. Im pretty new to linux, anymore help please?

edit -
I 'sudo nautilus' and seemed to be able to delete it... My disk space is still gone though...

---

### Post by P4man on 2009-08-22
/media/My Book is just a folder. Its the folder where ubuntu mounted your external harddrive to originally, but if I understand your situation right, your backup program later created that folder, and so ubuntu mounts the external drive to /media/My Book_ instead.

Anyway. disconnect the external drive to make sure you're not deleting the wrong stuff. boot from the cd. Then open nautilus file manager with root privileges. To do that, open a terminal and type:

```
gksudo nautilus
```

Locate the internal drive in the left pane (probably something like "160GB volume). Open it, it will be mounted automatically if all goes well. Then navigate that drive and go to /whateveryourinternaldive/media and delete the "my book" folder. Hold down shift key while pressing delete to remove it entirely without sending it to the recycle bin.

---

### Post by P4man on 2009-08-22
our messages crossed :)
Maybe the folder is now in the trash bin, see if you can empty it.
Im not too sure how to locate the trash on a mounted volume from a livecd, its usually in /home/yourusername/.local/share/Trash

the "." means its hidden, to show hidden hiles in nautilus, press control+H

Another idea might be to run disk usage analyzer now?

---

### Post by P4man on 2009-08-22
one more thing: always use **gk**sudo to launch a graphical program with root permissions. Sudo is for command line apps. gksudo for graphical app.  Running nautilus (or any other graphical program) with sudo can cause all kind of weird problems.

---

### Post by roffle on 2009-08-22
Thanks man :) 

So once I deleted it via 'gksudo nautilus' its put it in '/root/.local/share/Trash/files/My Book' but I cant seem to delete it from there... If I right-click it and go Move to garbage bin, it will just appear back in that folder with a different name like 'My Book2.2'...

---

### Post by P4man on 2009-08-22
select it and press shift+delete.
edit: btw, is that folder empty or not?

---

### Post by roffle on 2009-08-22
definately the right folder, it has the backup folders inside. 140-ish gb.

Im pressing shift+delete (backspace) but it doesnt do anything... Im assuming you mean shift+del which I havent got cause im using a Apple keyboard. Any other way?

---

### Post by P4man on 2009-08-22
lol, apple keyboards dont have shift or delete ? 
anyway,  open a terminal then type:

```
 sudo rm -rf /root/.local/share/Trash/files/My Book
```

Make sure you dont make any typo's, and be aware everything is case sensitive!! you can use autocomplete (tab key) to avoid typo's. Assuming apple's have a tab key :p

---

### Post by roffle on 2009-08-22
lol... they have shift just no delete :(

anyway, that seems to have done the trick! my free space is back and everything appears normal again! thanks heaps man :p

---

