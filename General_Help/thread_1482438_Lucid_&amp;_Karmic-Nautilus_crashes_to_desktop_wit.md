---
title: "Lucid &amp; Karmic-Nautilus crashes to desktop with 2 windows onscreen and &quot;Delete&quot; used."
date: 2010-05-13
forum: General Help
---

### Post by emarkay on 2010-05-13
I thought it was a Karmic thing, then a Lucid Beta thing, but still - I open w Nautilus windows in my "home" directory, and select a few files and then hit the "Delete" key; it then crashes to the desktop.

I have only noticed it lately as I have been transferring files across directories and drives and when it crashes, the transfer is left in "limbo" - no corruptions AFAIK, but the transfer stops obviously, and thus I have to reopen the windows, reselect the files and transfer, then wait for the transfer file indicator to finish, then delete.

This has happened about 10 times in the past few months, and just yesterday.

Both Karmic and Lucid are updated and this is in on the "clone" PC (MSI mainboard) in the sig.

I have not used the other PC's s enough to recall this issue.

---

### Post by emarkay on 2010-05-15
OK am I the only one here who uses the keyboard "DELETE" key - either with a selected group or in "rapid fire" presses of individual files?

This happened again today as I was copying files to an external USVB drive - although I have sen this just on the native PC.

---

### Post by emarkay on 2010-05-25
Oh, and on two different PC's.

Surely...  :0

---

### Post by emarkay on 2010-05-28
It doesn't even have to be 2 windows, just open a nautilus window, and start "rapid fire " hitting the DELETE key and tell me if it happens to you, to, please?

---

### Post by emarkay on 2010-06-02
One last time - Crashed another time in Lucid - deleting a bunch of files and hit the "Delete key" and wend immediately to the desktop, 2 windows open this time.

How can I file a bug report if I am seeing this on my systems and no one else is?

147 people have read this and I presume that they have tested their delete key and have not had this happen; it doesn't happen always, but maybe every second or third time as I recall.  Comment?

---

### Post by dino99 on 2010-06-02
some time ago i've reported on launchpad this problem (few months now) when i was using Del key to fast only. no fix known at time.

have you any errors logged ?

maybe cleaning the room might help: gconf-cleaner (yes to all), and bleachbit (as admin, but set your prefs carefully)

---

### Post by emarkay on 2010-06-03
Use Bleachbit - a great cleaner program.

What type of error would there be? 

Can you please get me the bug number so I can subscribe and add info as needed? 

Thanks.

---

### Post by UBM7Tablet on 2010-06-09
I for one can commiserate; I also experienced this issue for the first time after upgrading from 8 to 10.  Every once in a while Delete or Shift+Delete will crash Nautilus, after files are deleted when the file list is being updated/refreshed to show the folder contents without the deleted files.  

I haven't found a fix for the issue myself, but the following tip might help alleviate a little of the pain:  
I found that after setting the option:
System->Preferences->Startup Applications->Options->Automatically Remember running applications.
After a Nautilus crash, all the other previously open naulilus windows will automatically re-open (except for the one that had the crash)

I'm wondering if this is actually a display issue.  Initially after the upgrade to 10, I also had very frequent Nautilus crashes when dragging files.  This was (in)corrected by disabling window effects and removing Compiz.  

I'm using the most current/recommended proprietary NVidia hardware drivers, and haven't yet tried using earlier versions.

---

### Post by UBM7Tablet on 2010-06-09
Writing this reply stimulated some neurons and reminded me of a similar issue under version 8 w\ EXT4.  It was the "trash-crash" issue when emptying the trash.  It would occur if the trash folder became corrupt.  I found a relevant thread ([http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7605566](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7605566)) and executed the following shell command to see if I had any bogus items in my trash folder:

ls ~/.local/share/Trash/*

Even though my trash was empty, I did have an item in the "Trash/info:" folder.  So I emptied out the trash folder manually:

sudo rm -r ~/.local/share/Trash/*

(Fingers crossed; will reply if I still get further delete crashes)

---

### Post by 5oak on 2010-06-14
> **UBM7Tablet said:**
> Writing this reply stimulated some neurons and reminded me of a similar issue under version 8 w\ EXT4.  It was the "trash-crash" issue when emptying the trash.  It would occur if the trash folder became corrupt.  I found a relevant thread ([http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7605566](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7605566)) and executed the following shell command to see if I had any bogus items in my trash folder:

ls ~/.local/share/Trash/*

Even though my trash was empty, I did have an item in the "Trash/info:" folder.  So I emptied out the trash folder manually:

sudo rm -r ~/.local/share/Trash/*

(Fingers crossed; will reply if I still get further delete crashes)

This actually helped, thnx! Nautilus would crash when emptying the trash... Now it doesn't anymore.

---

### Post by UBM7Tablet on 2010-06-17
No additional DEL crashes since the manual trash folder cleanout so far...

Noticed an updated NVIDIA driver included in recent updates; may try re-enabling Compiz to see if dragging from Nautilus is functional again...

---

### Post by 5oak on 2010-06-22
> **5oak said:**
> This actually helped, thnx! Nautilus would crash when emptying the trash... Now it doesn't anymore.

Edit: hmmm it didn't after all... Same problem again. Please help...

---

### Post by UBM7Tablet on 2010-06-22
Unfortunately I also got another nautilus delete crash today, even though the trash folder is in a good state.

There was a background copy in progress to a USB storage device and the file was incompletely copied (3/4 length) due to the crash.  

Tried the same steps again; initiate copy to USB, then shift-delete files, but have not been able to reproduce the issue.

:(  Between this, the Nautilus drag-crash and stuck keys in VNC, I'm starting to pine for version 8.  


I'm going to try kicking off manual disk checks via System->Administration->Disk Utility

---

### Post by 5oak on 2010-06-23
Yeah Nautilus crashes almost always when emptying the trash, even without opening it but right-clicking and emptying...:s

---

### Post by UBM7Tablet on 2010-06-24
Has anyone ever gotten a delete-crash in other programs and/or file managers?

I ask because the drag-crash issue affects Nautilus *and* other apps such as GQView.  So far I haven't had a delete-crash in other applications.  

I'm going to try turning off safe-delete in GQView and using the Thunar file manager for a while.  If I get a delete-crash in either of those apps as well as Nautilus, it may indicate the fault is somewhere else.

---

### Post by UBM7Tablet on 2010-07-05
Been using Thunar file mgr for a couple of weeks; lots of deletions after burning CD & DVD images has not phased it.  

Switched back to Nautilus and almost immediately crashed when deleting a few 10s of MBs of files.  Must be a post-delete display issue, because files are always gone when I relaunch Nautilus and check...

---

### Post by emarkay on 2010-08-09
So is this a bug or what - looks like one. 

Filed: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/615428](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/615428)

I had Thunar, and liked the ability to bulk rename files - something not available natively, but it added a crapolaload of KDE things and was overly redundant with Nautilus there.

---

### Post by emarkay on 2010-08-21
Seems it's not an issue for anyone else...

---

### Post by emarkay on 2010-09-17
No action on this in a month.  

Since I don't know what else may be involved, I have just "trained" myself to not use the Delete key.  

Anyone who's seen this, please log in or register with Launchpad and Subscribe (and comment with specifics if possible) on this Bug, as the information I had when this happened was unsuable to the "Bug Team".

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/615428](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/615428)

---

