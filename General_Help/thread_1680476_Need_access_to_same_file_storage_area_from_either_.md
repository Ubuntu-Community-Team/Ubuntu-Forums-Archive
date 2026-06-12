---
title: "Need access to same file storage area from either XP or Ubuntu"
date: 2011-02-02
forum: General Help
---

### Post by BearDrummer on 2011-02-02
I have XP Professional and Ubuntu 10.04.1 installed in the side-by-side configuration on my son's computer.  I need to be able to access files stored cross partition, preferably both ways.  I am most interested in being able to access files stored in XP while I use Ubuntu.

I am trying to learn Linux while trying to wean the others in the house off Windows; they are resistant.  This means I need to be able to be able to access the same files from either operating system.

Any ideas how to accomplish this?

---

### Post by nd456 on 2011-02-02
you go to places/computer/filesystem/host and thats from Ubuntu to xp i don't know about the other way around
(my documents is under documents and settings)

---

### Post by topher-t-mill on 2011-02-02
You can access files in your windows partition from Ubuntu, you will be asked to use password.However to share files using windows you will need to make a separate FAT partition, which can be mounted by both OS's.It is an uphill struggle weaning folks off Windows.

---

### Post by ajgreeny on 2011-02-02
> **topher-t-mill said:**
> You can access files in your windows partition from Ubuntu, you will be asked to use password.However to share files using windows you will need to make a separate FAT partition, which can be mounted by both OS's.It is an uphill struggle weaning folks off Windows.
For safety's sake it is better to keep your XP partition separate from your data partition, so if it is not too much trouble, copy all your data files from XP to an external disk, then defrag a couple of times, then shrink XP using gparted on the live ubuntu CD, to make space for a new ntfs partition for your data (better than fat32).

You will still be able to access all those data files by default in windows, and can easily make that data partition available in ubuntu with a simple edit to /etc/fstab.

Come back for more details if and when you want to do this

---

### Post by oldfred on 2011-02-02
When I was first learning Ubuntu I did what ajgreeny suggested. I also moved my Firefox &  Thunderbird profiles into the NTFS shared partition (they are still there) and then when my wife wanted to check email or use Internet she did not have to reboot to XP. I still have one app and have said for at least a year I would convert that but still use XP a little.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

