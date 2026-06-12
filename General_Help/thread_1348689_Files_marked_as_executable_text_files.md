---
title: "Files marked as executable text files?"
date: 2009-12-07
forum: General Help
---

### Post by The Bright Side on 2009-12-07
All my text files and HTML files (and possibly others) are marked as "executable text files", so whenever I double-click on an HTML file, I will get the dialog asking me what I want to do (run in terminal, display, cancel, run).

Now, how do I get HTML files to open in Firefox on double-click? I can change the Properties of each individual file to "not executable", but that's quite a hassle... Same goes for text files. How can I open them with gedit by default?

Thanks!

(Ubuntu Karmic)

---

### Post by Vince N on 2009-12-07
Unfortunately you'll have to remove the executable flag from them to keep this from happening.  You should be able to do it in bulk using a select all command and then editing the properties or from the command line.

---

### Post by bodhi.zazen on 2009-12-07
> **The Bright Side said:**
> All my text files and HTML files (and possibly others) are marked as "executable text files", so whenever I double-click on an HTML file, I will get the dialog asking me what I want to do (run in terminal, display, cancel, run).

Now, how do I get HTML files to open in Firefox on double-click? I can change the Properties of each individual file to "not executable", but that's quite a hassle... Same goes for text files. How can I open them with gedit by default?

Thanks!

(Ubuntu Karmic)

This usually happens when using either FAT or NTFS. These file systems do not understans Linux permissions, and so permissions are set at the time of mounting.

You can use dmask, fmask, and umask to set permissions.

if you copied the files, use find and chmod a-x your files ;)

---

### Post by w0ipl on 2009-12-20
> **bodhi.zazen said:**
> This usually happens when using either FAT or NTFS. These file systems do not understans Linux permissions, and so permissions are set at the time of mounting.

You can use dmask, fmask, and umask to set permissions.

if you copied the files, use find and chmod a-x your files ;)

I don't understand. 
My problems with this started yesterday after installing the latest Firefox updates. 
How can files that have been in use for almost a year, now have problems, unless it came with the latest update?

---

### Post by bodhi.zazen on 2009-12-20
I do not know without additional information. What file system are you using ? ext3/4 ? fat ? ntfs ?

---

### Post by w0ipl on 2009-12-20
> **bodhi.zazen said:**
> I do not know without additional information. What file system are you using ? ext3/4 ? fat ? ntfs ?
Since it was a pre formatted HD I'll guess FAT32, I didn't verify it before loading. I loaded a new HD with Ubuntu about a year and a little ago.

As I said, all this started when I put up the latest Firefox (night before last -12/18 as I shut down ).

---

### Post by dcstar on 2009-12-20
> **The Bright Side said:**
> All my text files and HTML files (and possibly others) are marked as "executable text files", so whenever I double-click on an HTML file, I will get the dialog asking me what I want to do (run in terminal, display, cancel, run).

Now, how do I get HTML files to open in Firefox on double-click? I can change the Properties of each individual file to "not executable", but that's quite a hassle... Same goes for text files. How can I open them with gedit by default?


In Nautilus: Edit-Preferences-Behaviour and select the "View" option.

---

### Post by bodhi.zazen on 2009-12-20
> **w0ipl said:**
> Since it was a pre formatted HD I'll guess FAT32, I didn't verify it before loading. I loaded a new HD with Ubuntu about a year and a little ago.

As I said, all this started when I put up the latest Firefox (night before last -12/18 as I shut down ).

Well, as I said, it all depends on your file system, and almost certainly nothing to do with firefox. st cre. fat and ntfs partitions do not support linux permissions, and permissions are set when you mount the partition.

With linux native partitions (ext3, ext4, etc) permissions are set via chown and chmod.

See:[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

or man mount.

If you do not know what file system you are using, your first step should be to identify the file system. You can do this via gparted.

---

### Post by w0ipl on 2009-12-21
> **bodhi.zazen said:**
> Well, as I said, it all depends on your file system, and almost certainly nothing to do with firefox. st cre. fat and ntfs partitions do not support linux permissions, and permissions are set when you mount the partition.

With linux native partitions (ext3, ext4, etc) permissions are set via chown and chmod.

If you do not know what file system you are using, your first step should be to identify the file system. You can do this via gparted.

OK, I stand corrected. It is ext3.

I still do not understand how something like the dialog box suddenly begins, after a full year of not having it be a problem. 
In other words, a band-aid may "fix" it, but how do I repair the problem that has shown up?

Thanks,
 Pat

---

