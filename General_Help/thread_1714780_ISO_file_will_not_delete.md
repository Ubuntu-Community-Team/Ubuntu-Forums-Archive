---
title: "ISO file will not delete"
date: 2011-03-25
forum: General Help
---

### Post by Martym on 2011-03-25
Posted in the Mint forum too but it looks like no one is on that forum tonight :neutral:

Well he title is not technically true. It deletes just fine.  It's just that it shows up in /home/Jamers/Desktop again, in less than a second.

I was moving some pictures off a an old DVD and decided to place them on my desktop. That's where I noticed an iso file for Ubuntu there. I deleted it because I did not want it there, and already have a copy on disc. It deleted just fine then reappeared on the desktop. I tried deleting by using rm ubuntu-10.04.2-desktop-i386.iso and sudo rm ubuntu-10.04.2-desktop-i386.iso it goes away then reappeaars. I renamed it just i386.iso and deleted it. It comes back as ubuntu-10.04.2-desktop-i386.iso. When I look in trash there is over 4 GB of this iso file in there. I own the file and the permissions of the file, when it re-appears is -rw-r--r-- so that's what 644? I can do anything I want to the file (except permanently remove it).

Please help me get rid of the thing once and for all

---

### Post by drs305 on 2011-03-25
Try opening up your file browser and using SHIFT-DEL to remove it. That will bypass the Trash Bin if that is what is causing the problem. You could try doing the same with files in your Trash bin (~/.local/share/Trash).

Even though you said you owned them, you might also try opening the browser as root and using the same SHIFT-DEL technique. Also check root's trash bin at /root/.local/share/Trash/files.

---

### Post by Martym on 2011-03-25
Thanks for the quick reply!  

The methods listed did not work.  There is an option on right click called delete and it's shift + del  I did also try doing a physical shift + delete.  The file deletes just fine, then it is recreated.  If I go to the trash folder ~/.local/share/Trash there are several copies in there.  Under root the /root/.local/share/Trash/files directory is empty.

I can add and delete any other file into the folder without any issues.

Is there a file I can tail or some log I can view to see what is happening when I delete the file?

---

### Post by Habitual on 2011-03-25
Is it mounted ?

---

### Post by Martym on 2011-03-25
You know what, I am amazed.  My PC is up and running 24x7 and there was a torrent for the ISO running.  That was started at the beginning of the month and the application, Kget, was not showing up in my application bar.  Once I canceled the download the file deleted with no issues

---

