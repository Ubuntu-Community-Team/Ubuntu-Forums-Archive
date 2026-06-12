---
title: "How do I recover my data?"
date: 2012-09-29
forum: General Help
---

### Post by duncan12 on 2012-09-29
I accidentally deleted some data over a month ago. I have a Deja  Dup backup from before then. But I have not found a way to restore from it, so I've been sitting here with some of my home folder missing for over a month. I want to reinstall, but I don't want to without knowing I've got the data back.

Here's my situation:

[LIST]
[*]Data currently in home folder: some older data missing
[*]Deja Dup backup: newer data missing
[/LIST]

So I want to merge the two, **and have the ability to select from a list what files I want to restore** (because I would have deliberately deleted some things inbetween). This can be done in Nautilus with the *File -> Restore Missing Files* menu item, however this doesn't search recursively - it doesn't find items in subfolders. If I go into a subfolder and click Restore Missing Files more does come up.

I have a [question on Launchpad]("https://answers.launchpad.net/deja-dup/+question/207477"), which has more details on exactly what I want to do. Unfortunately, a month later there is still no answer on it.

I do have an external hard drive with lots of free space to experiment on (so I could, for example, create a folder called "old" in there, and restore the old backup into it, then do the merge using a different program)

I need ideas! Can anybody help?

---

### Post by kc1di on 2012-09-29
hi duncan12,

I've had pretty good sucess with a programed named scalpel it is
 in the repository.  Here a page with some info on it.

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/")

Good Luck

---

### Post by duncan12 on 2012-09-30
> **kc1di said:**
> hi duncan12,

I've had pretty good sucess with a programed named scalpel it is
 in the repository.

Hi,

It seems to me that is a program to recover deleted data from the disk. Surely, since I deleted them from the disk a while ago, it would be better to use my Deja Dup backup? I just need to find a way to merge the old backup with the current home folder.

Correct me if I'm wrong, but that's my understanding.

Thanks,
Duncan

---

### Post by HiImTye on 2012-10-01
[https://live.gnome.org/DejaDup/Help/Restore/LostFile](https://live.gnome.org/DejaDup/Help/Restore/LostFile)

---

### Post by paulkkarns on 2012-10-01
Hi,

I lost my Laptop very important data, I want to back this, HD problem in bios HD non..

---

### Post by Wim Sturkenboom on 2012-10-01
> **paulkkarns said:**
> Hi,

I lost my Laptop very important data, I want to back this, HD problem in bios HD non..
How does this help the OP?

A moderator will certainly tell you to start your own thread ;)

If your disk is dead, you're out of luck. Boot from a liveCD/liveUSB and see if the disk is recognized. If so, mount it, connect and external HD and backup your data.

---

### Post by Wim Sturkenboom on 2012-10-01
> **duncan12 said:**
> I just need to find a way to merge the old backup with the current home folder.
No experience with dejadup. Can't you just copy the backup back? If files already exist, it will prompt you and you can ignore.

Alternative might be a script, but you have to write it yourself ;)

---

### Post by duncan12 on 2012-10-01
> **HiImTye said:**
> [https://live.gnome.org/DejaDup/Help/Restore/LostFile](https://live.gnome.org/DejaDup/Help/Restore/LostFile)

From my OP:
> **duncan12 said:**
> This can be done in Nautilus with the File -> Restore Missing Files menu item, however this doesn't search recursively - it doesn't find items in subfolders. If I go into a subfolder and click Restore Missing Files more does come up.

Thanks for posting, but that link said to do what I've already tried and had a problem with, as said in my OP.

---

### Post by duncan12 on 2012-10-01
> **Wim Sturkenboom said:**
> No experience with dejadup. Can't you just copy the backup back? If files already exist, it will prompt you and you can ignore.


Hi,

I also have no experience with Deja Dup, but from what I understand a standard "restore" won't let me select from a list which files to restore and which to not.

---

### Post by HermanAB on 2012-10-01
DejaDup uses Duplicity as its backend, so you should look into Duplicity itself and also Duply, which is another front end for it.

[http://duplicity.nongnu.org/](http://duplicity.nongnu.org/)
[http://ftplicity.sourceforge.net/](http://ftplicity.sourceforge.net/)

...and since duplicity uses encrypted tar files, you should be able to untar them yourself and restore only what you want.

---

