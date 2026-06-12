---
title: "Can't copy my home folder to external drive"
date: 2009-10-09
forum: General Help
---

### Post by mjpatey on 2009-10-09
I'm stuck on this... I'm trying to back up my entire home folder (/home/mjpatey) to an external FAT32 USB hard drive.  I can't write to the external drive as a regular user because I haven't figured out how (but that's another story), so I try it with sudo, and get the following result:

```
mjpatey@zippy:/home$ sudo cp mjpatey /media/sdb1/JauntyHome
cp: omitting directory `mjpatey'

```

When I try doing it in nautilus, I essentially get the same result (using gksudo nautilus):

> Files in the folder "mjpatey" cannot be handled because you do not have permissions to see them.

When I check permissions for my home directory using Nautilus' "Properties" dialog, it shows that I own it and have read/write access to folders, can't access files at all (which isn't entirely true, as I save things there all the time).  When I try to change the permissions to allow read/write of files, they snap back to the previous value.

Incidentally, I also get a strange message at login saying my .dmrc file has the wrong permissions.  I tried:

```
chmod 644 .dmrc
```

...but it hasn't allowed me to copy my home directory to the external drive, or change the file access permissions of my home directory.

Any idea how to fix my broken home folder permissions, so I can copy my home folder to the external drive?

Thanks in advamce for any light you can shed!

-Mark

---

### Post by drs305 on 2009-10-09
I wrote this guide a while back on solving .dmrc issues. Run through the steps to fix that problem and see which still remain once you have corrected it:

[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")

---

### Post by rippin on 2009-10-09
> **mjpatey said:**
> I'm stuck on this... I'm trying to back up my entire home folder (/home/mjpatey) to an external FAT32 USB hard drive.  I can't write to the external drive as a regular user because I haven't figured out how (but that's another story), so I try it with sudo, and get the following result:

```
mjpatey@zippy:/home$ sudo cp mjpatey /media/sdb1/JauntyHome
cp: omitting directory `mjpatey'

```When I try doing it in nautilus, I essentially get the same result (using gksudo nautilus):



When I check permissions for my home directory using Nautilus' "Properties" dialog, it shows that I own it and have read/write access to folders, can't access files at all (which isn't entirely true, as I save things there all the time).  When I try to change the permissions to allow read/write of files, they snap back to the previous value.

Incidentally, I also get a strange message at login saying my .dmrc file has the wrong permissions.  I tried:

```
chmod 644 .dmrc
```...but it hasn't allowed me to copy my home directory to the external drive, or change the file access permissions of my home directory.

Any idea how to fix my broken home folder permissions, so I can copy my home folder to the external drive?

Thanks in advamce for any light you can shed!

-Mark

Did you set root to login when installing? ~/.dmrc is your display manager RC file listing what is your preferred desktop (GNOME, KDE, etc.). I'll bet when you switched to sudo for cp your files, root became owner. Back out to tty1 (ctrl+alt+F1), login, sudo su (give full root access), then chown -hR <user>:<user> /home/<user>/* . Next, ls -la /home/<user>/* | less  (or if you don't have 'less' use 'more') to check permissions.
After your can use your /home, test for your 'groups' and rights for USB external drive.

---

### Post by mjpatey on 2009-10-09
drs305, thanks for the excellent guide!  I've bookmarked it.

I did everything it suggested, and it all appeared to "take"... but I still can't copy my home directory:

```
 mjpatey@zippy:~$ sudo cp /home/mjpatey /media/sdb1/Jaunty
cp: omitting directory `/home/mjpatey'
```

...and now I can't even check permissions for the home directory at all.  When I right-click on it in Nautilus, almost everything is grayed out, including "Copy" and "Properties".  I can check from a sudo Nautilus window, and it shows the same permissions as it did before I followed the guide (no file access at all).

I'm still stumped.

---

### Post by dcstar on 2009-10-09
> **mjpatey said:**
> I'm stuck on this... I'm trying to back up my entire home folder (/home/mjpatey) to an external FAT32 USB hard drive.  I can't write to the external drive as a regular user because I haven't figured out how (but that's another story), so I try it with sudo, and get the following result:
.........
Any idea how to fix my broken home folder permissions, so I can copy my home folder to the external drive?

Thanks in advamce for any light you can shed!


[LIST=1]
[*]Your cannot use another user (sudo) to copy your own files.
[*]Fix the mounting issue with the drive and you will have no problems doing things normally.
[*]What have you changed to break the external drive mounting?
[/LIST]

---

### Post by mjpatey on 2009-10-09
OK, I did what rippin suggested (thanks!) and now have the ability to at least "Copy" and get Properties from my home directory.  When I look at its properties, they still show I have no file access permissions whatsoever.

Until that's fixed, I do need to fix permissions on the external drive (as dcstar suggested), so it will mount during boot.  Should I start a new post for that, or is this a quick fix?  The problem I'm foreseeing is that it's formatted as FAT32 (actually, VFAT... same thing, I think).  FAT32 doesn't support permissions, does it?

---

### Post by egalvan on 2009-10-09
> **dcstar said:**
> [LIST=1]
[*]Your cannot use another user **(sudo)** to copy your own files.
[/LIST]

So root cannot copy any file not owned by root?
I thought root "owned" everything.
(which is why we are always warned to be careful of file operations done as root)


Further, I just did

```
ernest@gx280:~$ sudo cp installed-software /installed-software

```

and the file (owned by 'ernest') appeared in the root of the drive,
and this copy is owned by root.

---

### Post by rippin on 2009-10-09
> **mjpatey said:**
> OK, I did what rippin suggested (thanks!) and now have the ability to at least "Copy" and get Properties from my home directory.  When I look at its properties, they still show I have no file access permissions whatsoever. <snip> 


Now that you're on your Desktop, you can open a file management tool as root and change all your ~/ files to your user and your group (the chown should have done that, tho').  Don't forget the executable bit for directories.

---

### Post by mjpatey on 2009-10-09
Rippin, thanks.. I have no idea how to do that, though.  Just gksudo nautilus, then Properties --> Permissions?  When I do that, my changes instantly revert once applied.

---

### Post by nothingspecial on 2009-10-09
> **mjpatey said:**
> drs305, thanks for the excellent guide!  I've bookmarked it.

I did everything it suggested, and it all appeared to "take"... but I still can't copy my home directory:

```
 mjpatey@zippy:~$ sudo cp /home/mjpatey /media/sdb1/Jaunty
cp: omitting directory `/home/mjpatey'
```

...and now I can't even check permissions for the home directory at all.  When I right-click on it in Nautilus, almost everything is grayed out, including "Copy" and "Properties".  I can check from a sudo Nautilus window, and it shows the same permissions as it did before I followed the guide (no file access at all).

I'm still stumped.

You need an -r in there.

A -v is always nice too.

```
sudo cp -rv /home/mjpatey /media/sdb1/Jaunty
```

-r will copy recursively, it won`t work otherwise.

-v will tell you what you are copying.

---

### Post by mjpatey on 2009-10-09
nothingspecial, thank you.  Your signature quote could not be truer!!!

Thanks to everybody here.  I was in a bit of a time crunch last night (EST), and finally decided to try the copy operation using a Live CD.  It worked like a charm, of course!

Another note: my reason for copying the home folder in the first place was to prepare for a new installation of the Karmic Beta, which I've now installed, and am posting from right now.  Of course, all permissions issues are now gone.  :-)  However, every time I've booted so far, I get an error regarding the external USB hard drive mentioned in this thread.  And although it mounts automatically, it takes FOREVER to open the drive in Nautilus.  Partitioning during installation also took forever, thanks to that drive's presence.  I almost aborted and restarted with it unplugged, but decided I'd stick it out.

Thanks again to everybody who answered in this thread!  It's been very educational for me.

-Mark

---

