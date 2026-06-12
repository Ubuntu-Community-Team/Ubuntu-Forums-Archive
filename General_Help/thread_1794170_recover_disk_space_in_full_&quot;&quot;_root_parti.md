---
title: "recover disk space in full &quot;/&quot; root partition"
date: 2011-06-30
forum: General Help
---

### Post by dragonfly41 on 2011-06-30
I have ubuntu 10.10 installed in separate "/" and "/home" partitions (plus some other partitions for Vista and ntfs shared data in a dual boot configuration).

I allocated 10 GB to "/" partition but it's filling up.

I'm now seeing warning messages .. with space available filling up .. 

"the volume filesystem root has only 78.8 MB space remaining"

Snapshots of disk usage from disk utility and gparted are attached.

I've got this link to read ..

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

What folders in root partition should I start to purge?   Logs, cache etc.

---

### Post by jerrrys on 2011-06-30
download "bleachbit" from the software center.  first use it as root, then as user.  also follow all recommended popups.  this may buy you a gig...

---

### Post by fixitdude on 2011-06-30
Did you search first?

[http://ubuntuforums.org/showthread.php?t=1774876](http://ubuntuforums.org/showthread.php?t=1774876)

---

### Post by SeijiSensei on 2011-07-01
Start with "cd /var; du -s *".  /var/log is probably a good bet.  /var/cache/apt/archives is another place to look.

---

### Post by jerome1232 on 2011-07-01
This will give you a good top level estimate and which folders are using alot of space.
```
sudo du -hx --max-depth=1 /
```


That being said I noticed your /var is like 3 GB's, which is huge, errant log perhaps? Dig around in there see if a log is unusually large.Try cleaning out apt-get's archives as well.

```
sudo apt-get clean
```

---

### Post by drs305 on 2011-07-01
You might also unmount all your devices/partitions mounted on /media. It's possible there are files directly written on /media that were meant to be written to another device.

Here is a guide for troubleshooting disk space issues. Common problems are backups made to / instead of a backup device, unemptied trash, and large log files.
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by gdonwallace on 2011-07-01
You might want to check /var/log/ directory.  During startup and when some processes and programs are started, a log is created.  It is not unheard of for /var/log to get full due to the log files.

Start Terminal --> cd /var/log --> du --max-depth=0 will scan just the first level of directories and report the size.  In that same directory you can also try ll -h to do a long listing of the directory in "human readable" format, will also help in finding files that have gotten larger

---

### Post by dragonfly41 on 2011-07-07
Thanks for the tips ..  but I've hit a problem with my '/' root partition (10 GB) being completely full ..

I can't login .. I get an error message 'GNOME Power Manager is not configured'.

Using ubuntu 10.10 liveCD I can view the mounted 10 GB filesystem .. (the root partition)

but I can't right click on individual folders/files in the 10 GB filesystem to Move To Trash to release space.

I installed temporary GNOME commander in liveCD to try to delete files but I get 'access denied' when I try to delete selected folders/files.

How do I clear out space from the mounted 10 GB partition?


[P.S.]

I've read this thread.

[http://ubuntuforums.org/showthread.php?t=1797914&highlight=gnome+power+manager](http://ubuntuforums.org/showthread.php?t=1797914&highlight=gnome+power+manager)

---

### Post by drs305 on 2011-07-07
From the LiveCD, you should be able to mount your Ubuntu partition and then open a file browser as root. 

```
sudo mount /dev/sdXY /mnt  # Example: sudo mount /dev/sda5 /mnt
gksu nautilus /mnt
```
CTRL-h to see hidden files.

Navigate to the files you want to delete, highlight them, and use SHIFT-DEL to make them go away. Include /mnt/home/<username>/.local/share/Trash and /mnt/root/.local/share/Trash in the folders you delete.

---

### Post by dragonfly41 on 2011-07-07
Thanks again .. I'm in ubuntu liveCD .. root partition mounted .. file manager .. highlight file .. but SHIFT-DEL has no effect !!

---

### Post by gizmo720 on 2011-07-07
In the live cd, type ```
sudo nautilus
```
The window that opens should be able to delete files.

---

### Post by dragonfly41 on 2011-07-07
I'm afraid not .. see attached snapshot of nautilus showing my 10 GB root partition mounted ..

but I'm not still the owner of any of the content viewed in nautilus

Right click and 'move to trash' is grayed out.

I still don't know why the tip to use SHIFT-DEL to delete files doesn't work as suggested earlier.


[EDIT]

seems that **[COLOR=Navy]gksudo nautilus[/COLOR]** gives me permission to trash content in mounted 10 GB root partition.

And .. SHIFT-DEL now works in gksudo mode.


Finally I managed to purge 3GB + from "/" partition (from 10 GB to 7 GB). 

also ran command ..  sudo apt-get remove gnome-power-manager

I'll keep an eye open for space used in "/".

---

### Post by fixitdude on 2012-03-18
You can also use the partition manager (with some trouble) to make the / partition bigger. It's not a lot of fun but it can be done. Back up all your files of course.

---

### Post by NotebookNerds on 2012-03-18
> **fixitdude said:**
> It's not a lot of fun but it can be done. 

It's not a lot of fun, you are right... but from what I have read he doesn't have many options left so this is definitely the best one to choose :)

---

### Post by Elfy on 2012-03-18
Old thread closed.

---

