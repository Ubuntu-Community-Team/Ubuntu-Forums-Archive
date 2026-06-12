---
title: "Partition/ Hard Drive Imaging"
date: 2009-12-05
forum: General Help
---

### Post by mikeody on 2009-12-05
I was chasing this issue a while back but I think we strayed away from my original question !
As an 'escapee' from Windows I am naturally nervous about back-ups - I dont sleep unless I know I can restore everything IF NECESSARY.
I have read a lot but am still unsure about what I should use. 
Sure, things like rsync are talked about but for a Linux newbie at this stage they seem a little 'heavy duty' for me - the last thing I want [IF I did need to restore a partition or whole disk] is to find I have screwed it up when I created it and I really dont have a back up !!
Windows of course has tons of similar 'whole disk' back up software available, but what should I use for Ubuntu ?
PartImage looks possible - has anyone used this and does anyone know of other options that preferably [for now at least] have a GUI to help me ?
Thanks.

---

### Post by SecretCode on 2009-12-05
**Clonezilla** helps me sleep at night!

---

### Post by ajgreeny on 2009-12-05
Now that I am very comfortable with linux and ubuntu in particular, I don't bother with a full disk image style backup, but find that, as it is so fast and relatively simple to install the whole OS from scratch, I simply backup all my home partition/folder to a USB hard disk formatted to ext3, not fat32, as they usually are.  The ext3 format is much better, and essential for permissions etc to be retained.

To do that I use either rsync in cli, which is actually very simple and not really to be feared, or grsync if a GUI is needed.  grsync has one or two fewer options, but is perfectly good for incremental backups of home.  Have another look and you may see how easy it is.

---

### Post by mikeody on 2009-12-05
Thazks for that but a question.
What about the various applications that you have installed/ modified etc etc ?
Surely a new reinstall with just Home available to copy back, although giving you a new OS, will still leave you with heaps of work to do to get it back to as it was ?
Or have I missed something really fundamental to Linux that doesnt applly in Windows ?

---

### Post by kaibob on 2009-12-05
> **mikeody said:**
> Windows of course has tons of similar 'whole disk' back up software available, but what should I use for Ubuntu ?

Another vote for clonezilla. It doesn't have a GUI, but the program is easy to use once you do a few backups. If you use ext4 file system, be sure to use the karmic-based version.

[http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla](http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla)

---

### Post by ajgreeny on 2009-12-06
> **mikeody said:**
> Thazks for that but a question.
What about the various applications that you have installed/ modified etc etc ?
Surely a new reinstall with just Home available to copy back, although giving you a new OS, will still leave you with heaps of work to do to get it back to as it was ?
Or have I missed something really fundamental to Linux that doesnt applly in Windows ?
Yes, I suppose you are right but it all takes so little time to add all the additional apps that I have installed even after a year or so that I find I can do it all quite quickly.  I admit I have no experience of making a clone of a whole drive so can not say if it is quicker than my method or not.  I'm sure it would probably be a lot quicker if I knew what I was doing to do it your way, but how often do you need to make a cloned backup, and how long does that take?  I have no idea.

There is also, incidentally, a quick way to get all current apps back using the command line and dpkg:-

HowTo: Create a list of installed packages and output this information to a file in your home directory you would use,
```
dpkg --get-selections > installed-software
```
And if you wanted to use the list to reinstall this software on a fresh Ubuntu setup,
```
dpkg --set-selections < installed-software
```
followed by
```
dselect
```

---

### Post by audiomick on 2009-12-06
Here are a couple of threads on the topic of saving what you have installed.

[http://ubuntuforums.org/showthread.php?t=1330184](http://ubuntuforums.org/showthread.php?t=1330184)
[http://ubuntuforums.org/showthread.php?t=1300029](http://ubuntuforums.org/showthread.php?t=1300029)

---

### Post by mikeody on 2009-12-06
Thanks everybody for your input.
I have downloaded the Clonezilla Live CD [approx 100MB] and am sleeping well !
I have tested it by creating images as follows :
- Single drive with XP and Karmic dual booted,
- Two drives - XP on one and Karmic on the other, dual booted,
- Two drives - Vista on one and Karmic on the other, dual booted.
All were imaged to an external NTFS formatted USB hard drive and all worked perfectly. Reasonably quick and doesnt image unused disc space.
I have tested the restore on all the above and it was great.
Although its not as fancy as some Windows back up software, the questions asked during the process are very intuitive and best of all it impresses your friends as all that text flies by on the screen !
One important thing for me is that it is a bootable CD so if for some reason I just cannot get into the system I can still do an image restore.

---

