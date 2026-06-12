---
title: "Shared data partition (Maverick - Vista)"
date: 2010-12-09
forum: General Help
---

### Post by Soldier2580 on 2010-12-09
Hi, as you may see, this is my first post on this forum, though i have been here more frequently :) I am quite the noob in ubuntu, but god, how i love it!

So Much for the intro. I Have got a dualboot on my machine, running Vista and Ubuntu 10.10, and now i have created a new partition, one that should be a data partition that holds data for both windows and ubuntu. I followed a how-to to get me to this point where i am stuck. My new partition has now some of the user subfolders (Pictures, Videos, Downloads) that i want in it, and windows is linked to them, but i cant seem to get ubuntu to change too..

So [this is the how-to i followed]("http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/")

it says:

> Open up terminal and enter the following command:

```
gedit .config/user-dirs.dirs
```

This is the file where your “special” folders in your home directory are defined. 

You can edit this to your liking.  In place of where you see “$HOME/Downloads” you would put in an absolute folder location, like “/media/storage/Downloads”.  Go ahead and create those folders, or whatever folders you’d like to call them, and put the path down for each of these. 

Click save, and we’re done the crux of the configuration.  You may need to reboot for these changes to take effect, but you can just boot into Windows to finish out the process in the next section.


This all works, only problem is: this thing doesn't seem to be saved when rebooted. How can i fix this?

Thanks!

---

### Post by Soldier2580 on 2010-12-11
bump?

---

### Post by VCoolio on 2010-12-11
Try 'xdg-user-dirs-update' after editing that file. Also show us what it looks like after you edit it.

Edit: also, welcome to the forums. And good way of asking a question, much better than a oneliner 'help this doesn't work' that a lot of newcomers post. Kudos.

---

### Post by Soldier2580 on 2010-12-11
Wow, that command you gave me is so helpful! I had to reboot every single time to check if it worked..

It kept giving me > "media/Wuntu/Documents was removed, reassigning DOCUMENTS to homedir" but I noticed I forgot to write a "/" in front of media, that must have been it.

The tutorial said to automount the new partition (Wuntu), so it would appear in the Places-tab (by changing the fstab etc). It was already there, so i didn't do those steps at first, but that didn't really work, that changed all userdirs to "$HOME".

Now when i restart, all of the directories are still set to the new location, as they should be. (as in the attachment)

But the links in the Places-tab still open the old folders, not the ones i made on the new partition. And there is now two different icons for Wuntu in the Places-tab, the first takes me to the folders on it, and the second one gives me: > Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command. I've attached a print of this, too, maybe that helps..

And thanks for the welcome! :D

---

### Post by cpmman on 2010-12-11
As my W7 partition was mostly unused after many defrags and Windows shrink I use e.g.

```

 Use Windows NTFS partition as storage for Linux
 
 cpmman@CQ61:~$ ln -s /media/W7/Documents\ and\ Settings/cpmman/Pictures ~/Pictures/W7
```after creating a W7 directory in each of Documents Pictures Music etc.

Just mount the W7 (or whatever label) to make it function.

---

### Post by Soldier2580 on 2010-12-11
cpmman, thank you for your reply :) I used your code on my 'Pictures'folder. I've learnt that ls is softlinking those directories, so that is probably exactly what i need, however, I can't see any changes or figure out how they are now linked..

---

### Post by cpmman on 2010-12-12
The soft link means that any files stored in the W7 "folder" on the Windows partition is visible and accessible on your ubuntu partition from any programme (e.g. Nautilus)  after mounting the Windows partition (again Nautilus - Places - W7 {partition} will mount it).  The files are read/write providing both users (in my case both called cpmman) have read/write(and execution) permissions in both partitions. I have found that even .exe files _may_ run in wine. Adobe Photoshop Elements runs and is used to edit photographs on my machine where it loads and saves to the designated folder but is also accessible from Picassa or any other photo edit/store program such as the online Windows Live Photos run from ubuntu Firefox. This method allows using the W7 partition for local storage and the 25Gb of Windows Live storage as online storage. It may be that some online programmes or non-Wine compatible programmes may not work with the soft link but I have not needed to test all the possibilities e.g. Adrive (50Gb), Dropbox, ubuntuone, gspace in Gmail or other ssh/ftp programmes to check that permissions are protected.

My main aim was to ensure that I only need to store one copy of each file locally which also reduces the size of the clonezilla backups I take regularly (and which can be stored on an external USB disc or online if needed). It may be a "belt and braces" system but I have found it to be an excellent substitute for the lack of "rollback" facility in ubuntu when I am testing pre-Alpha versions of OS.

---

### Post by Soldier2580 on 2010-12-12
It works! I got it as i wanted it! :D I put softlinks in the home directory, linking to my new partition, and i changed the user dirs a little, because i changed some names. 
But it works perfectly! The links at the side of nautilus and the  docky folders take me directly to the folders in my new partition, and they have their special folder icons again! :D 
Just gotta love this forum.

Only thing i was wondering.. I now use softlinks in the userdirs config like so.. 

```
XDG_MUSIC_DIR="$HOME/Music"
```
(with home/user/Music being a softlink the a folder on another partition)


Is that a problem? Because of what I've read, softlinks are actually folders too, right? So far everything works great, but can this be a difficuly in the futurre?

---

### Post by cpmman on 2010-12-12
I do not know if the XDG system conflicts with the "soft links" (properly called symlinks i.e. symbolic link to). Perhaps VCoolio or someone else knows or you may wish to google for an answer. If you leave this thread open someone else may be along to help you but otherwise please mark your thread "Solved" by using the Thread Tools at the top of the page when you are satisfied.

Glad to help - I have found solutions to all my queries by reading this excellent forum.

---

### Post by Soldier2580 on 2010-12-12
Well, it seems to me that my problem is solved, so I'll mark it accordingly :) If there should be any further problems with it, then I'll be back :p or of course, if what i did here is dangerous for some reason, pm me! :)

Thank you very much!!!!

---

