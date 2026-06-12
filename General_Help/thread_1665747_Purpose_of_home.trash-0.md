---
title: "Purpose of home/.trash-0 ???"
date: 2011-01-12
forum: General Help
---

### Post by tsucol11 on 2011-01-12
Using Ubuntu 10.04 64 bit. 

System working great except I was slowly loosing space on the /home partition. I finally located 17 gigs of data, which I had deleted, _a long time ago_, in the  home/.trash-0 subdirectory.

1st question --why wasn't this data deleted months ago when I "supposedly deleted" the files & emptied the trash bin?

2nd question why didn't the "Disk usage analyzer" indicate that most, if not all, the partition was being used by files in the home/.trash-0 subdirectory.

This is somewhat annoying. Is there a way to properly empty all trash bins in including the various hidden .trash bins in one shot.

Thank you for your assistance & all the good tips in the past.

Brian

---

### Post by tsucol11 on 2011-01-12
> **tsucol11 said:**
> Using Ubuntu 10.04 64 bit. 

System working great except I was slowly loosing space on the /home partition. I finally located 17 gigs of data, which I had deleted, _a long time ago_, in the  home/.trash-0 subdirectory.

1st question --why wasn't this data deleted months ago when I "supposedly deleted" the files & emptied the trash bin?

2nd question why didn't the "Disk usage analyzer" indicate that most, if not all, the partition was being used by files in the home/.trash-0 subdirectory.

This is somewhat annoying. Is there a way to properly empty all trash bins in including the various hidden .trash bins in one shot.

Thank you for your assistance & all the good tips in the past.

Brian

Just tried to delete the home/.trash-0 subdirectory files using "gksudo nautilus". Permissions state that files belong to root and will not permit me to delete same using admin privileges. 

Perplexing behavior

Brian

---

### Post by tsucol11 on 2011-01-12
> **tsucol11 said:**
> Just tried to delete the home/.trash-0 subdirectory files using "gksudo nautilus". Permissions state that files belong to root and will not permit me to delete same using admin privileges. 

Perplexing behavior

Brian

cd /home
ls -a
sudo rm -r .Trash-0

Above worked well. questions 1 & 2 remain.

Thank you

Brian

---

### Post by drs305 on 2011-01-12
If the trash belonged to root you as a normal user can't touch it. Think of deleted files in the trash bin just as ordinary files. They still exist; they still take up space; and they have just been moved to subfolders in a special folder called 'Trash'.

The .Trash-1000 folder holds 'trash' deleted from non-linux filesystems. The number is from the uid - each user has one; the first user created is normally 1000, thus .Trash-1000. Trash belonging to the user and deleted from a non-linux filesystem (e.g. ntfs) resides in .Trash-1000 folders but can be seen in the user's normal Trash icon.  *If* the .Trash-1000 contents are seen in the user's trash bin, they will be removed when the user empties the trash.

Files deleted by root using a file browser go to root's Trash bin in /root/.local/share/Trash (subfolders files and info). Only root can delete these files and emptying the user's Trash bin won't delete the files nor free up the disk space. 

If you use a file browser to delete the Trash or sub-folders, use SHIFT-DEL. Using DEL will just move them back to ..... Trash!

You can easily make up a command to remove all the user's trash. I prefer removing root trash with a file browser, as using 'sudo' and 'rm' together can have very serious consequences if you put a space in the wrong location.

You can find all your Trash bins with this command:
```
sudo find / -type d -name *Trash* 
```

[Trash]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by JOHNNYG713 on 2011-01-12
There is also a "Delete" option that bypasses trash, open a nautilus window goto edit>preferences, click the "Behavior" tab then tick the "add a delete command that bypasses trash" ! This will be an option when you right click on something you want to get rid of ! But be careful !!  There is no going back once you have deleted somting ! This option can also be added to sudo nautilus and gksudo nautilus!

---

### Post by tsucol11 on 2011-01-12
Thank you DRS305 & JOHNNYG713

I now realize that when using gksudo nautilus and deleting files from system users (file management) , these files go to /home/.Trash-0. As such they do not appear in the trash bin on the bottom panel and a user can mistakenly believe they have been completely deleted.

I have set the delete option that bypasses trash in both nautilus & gksudo nautilus and will monitor the hidden trash bins more closely.

I have regained 17 gigs of free space + deleted files I thought were long gone.

Good learning experience.

:popcorn:

Brian

---

