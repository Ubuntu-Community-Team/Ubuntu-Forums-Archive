---
title: "Incorrect partition size"
date: 2006-04-19
forum: General Help
---

### Post by lucia_engel on 2006-04-19
According to Baobab, I've used up 350mb of my 4gb /home partition. This seems about right by my own calculation. But when I'm using, nautilus, disks manager, or gparted, they list that I only have 1.9gb free. Here's my df -h output:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             4.9G  2.5G  2.2G  54% /
tmpfs                 245M     0  245M   0% /dev/shm
tmpfs                 245M   13M  232M   6% /lib/modules/2.6.12-10-686/volatile
/dev/hda9             3.9G  1.8G  2.0G  48% /home
/dev/hda1             5.9G  4.2G  1.8G  71% /media/hda1
/dev/hda5              55M  4.3M   51M   8% /media/hda5
/dev/hda6             3.9G  2.2G  1.8G  56% /media/hda6
/dev/hda7              34G  5.9G   29G  18% /media/hda7
/dev/hda8             2.5G  2.1G  421M  84% /media/hda8

So how can I check what is taking up half my space?

---

### Post by dave9191 on 2006-04-19
You can use the disk usage program (du)

du -h --max-depth=1

the max depth flag will mean that it will only list files and dir in the current directory. Rather then listing all files and sub directories which can be overwhealming to look through. It will give you the total space used by that dir and its files and sub directories. 

Hope that helps. 

--
Dave

---

### Post by lucia_engel on 2006-04-19
Thank you, I used that and saw "du" blocked on /home/.Trash-root, after I switched over to root and used the command again, it listed 1.4gb in .Trash-root. So I went in the the folder with "gksudo nautilus" and found all these crap that I emptied from my recycle bin are still there.

Is this suppose to be default?

When I tried to select all in .Trash-root to delete the files from trash, it didn't work, but right clicking on them on file at a time does.

I found a command in Ubuntu Guide:

sudo rm -fr $HOME/.Trash/

I'm guessing it's safe to use this command on the .Trash-root directory too?

Edit to add: Found this post "[Where is my free space?]("http://ubuntuforums.org/showthread.php?t=37327")" that had the same problem. So I'm guessing this is the default. Is there a way I can auto execute those rm commands at shutdown (as oppose to Session -> Startup")?

---

### Post by bollix47 on 2006-04-19
You could just right-click on the trash icon (bottom right corner of screen) and select "Empty Trash".

---

### Post by lucia_engel on 2006-04-19
The trash bin (applet and the desktop icon) is empty. But I'm assuming the stuff that I emptied out moved the .Trash and .Trash-root too.

---

### Post by dave9191 on 2006-04-19
The trash can icon in the corner is for your .Trash dir. .Trash-root would be things that you deleted as a root user in nautilius. When you delete a file in nautilus it is moved to the trash by default.

sudo rm -fr $HOME/.Trash/

will delete all the files in Trash as the root user so there wont be any permision problems. You can use the same thing for trash-root folder as well. 

You could have the commands run at logout or system shutdown if you want your trash to be emptied every time you shutdown. But I am too tired to try and figure it out and suggest you start a new thread about running a command on shutdown. I guess that I would try and put a script into the /etc/init.d folder that is run on shutdown. But don't mess around with those unless you know what you are doing :)

And just a few extra notes:
 - If you use the rm command, it deletes files stright away, and doesn't put them in a trash can. 
 - Nautilus uses .Trash as the trash can folder. 
 - There might be one for the root user in /root/.Trash as well. 
 - If you use a different file browser then nautilus it may not have a trash can function or may use a different folder. 
 - The trash can icon on the panle is only for the .Trash folder. 

--
Dave

---

### Post by lucia_engel on 2006-04-19
I see, thanks for clearing that up. I guess I'll just leave it be and remember to clear the root trash once in a while (though I don't remember deleting so many stuff in root).

---

