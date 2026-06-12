---
title: "Permissions could not be determined"
date: 2006-04-23
forum: General Help
---

### Post by Minn3h on 2006-04-23
I was changing the permissions of a large number of files at a time in Nautilus file browser thing and the program just ended.  Now all of those files and folders are of unknown size and the permissions tab says "The permissions of '<file name>' could not be determined."  Is there a way to rescue my files and folders?  Not to mention the folders are now just files so I have no idea about the files that "are" inside them.

---

### Post by David Haas on 2006-04-23
Minn3h--It would probably be easier to fix up your file's permissions in the Terminal, if your comfortable with it. If not, you'll find it very useful to work more with it. 

In the directory (folder) of interest to you, enter the ls -l command to see all the files and directories therein listed with their permissions. Then you can use the chmod command followed by the file name to change permissions, as in chmod u+w <filename> to give the file's user (you) write permission. You may need to type sudo before chmod to change some files. 

Well, enough for now. Get back to the forum if you need elaboration on this.

David

---

### Post by Minn3h on 2006-04-24
Thanks for your reply, it helped me realize that the affected folders had had their execute permission removed for owner and that caused the bizarre appearance of files and folders contained within.  It was simply a matter of taking all those folders and rechecking the appropriate execute box.

---

### Post by Shampyon on 2007-04-24
Resurrecting a dead thread. I'm having this problem. Because the permissions can't be determined for several files, they can't be written to. So far I've only noticed it causing problems in Firefox, specifically in the following:
```
?---------  ? ?   ?         ?                ? fireFTPsites.dat
?---------  ? ?   ?         ?                ? gmanager
?---------  ? ?   ?         ?                ? history.dat
?---------  ? ?   ?         ?                ? hostperm.1
?---------  ? ?   ?         ?                ? install.log
?---------  ? ?   ?         ?                ? mimeTypes.rdf

```
All the other files in the output look like this:
```
-rw-rw-rw-  1 tay tay     100 2007-04-23 21:53 blocklist.xml
drwx------  2 name name     288 2007-04-24 17:00 bookmarkbackups
-rw-rw-rw-  1 name name 1303106 2007-04-24 17:08 bookmarks.bak
-rw-rw-rw-  1 name name 1303106 2007-04-24 17:08 bookmarks.html
drwx------  2 name name   16624 2007-04-24 17:11 Cache
drwx------  4 name name      96 2007-04-23 21:45 Cache.Trash

```
(Username changed for safety, of course)

I've tried solutions already mentioned in this thread, both as normal user and root, to no avail. Is there any way to force a reset of the permissions of these files?

---

### Post by rouben on 2008-02-15
Could be an issue with a corrupt filesystem... I suggest running fsck manually. If you've never done it before, I suggest reading up on the topic, since I don't think there are any GUI tools out there to control that... I might be wrong though.

---

