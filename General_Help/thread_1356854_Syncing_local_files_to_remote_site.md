---
title: "Syncing local files to remote site"
date: 2009-12-16
forum: General Help
---

### Post by thomashw on 2009-12-16
I have a lot of documents on my home desktop and would like to have them synced to my web space. I don't own the server so I can't install anything on it.

I've tried rsync but I believe it would need to be installed on the server (can't do), and I also couldn't find any information/examples on how to do it.

I found a program called mirrordir and I used its copydir function. It's supposed to sync files, but each time it kept overwriting files that were already there (which it isn't supposed to do.) It would also disconnect from the server before it was done uploading.

If you guys have any suggestions I'd love to hear them. I want to keep the files on my server and would rather avoid using something like Dropbox or PowerFolder.

Thanks!

---

### Post by ajgreeny on 2009-12-16
> I've tried rsync but I believe it would need to be installed on the server (can't do), and I also couldn't find any information/examples on how to do it.
Are you sure about that?  Surely if you can navigate to a specific folder on the server, you can also use rsync.  Perhaps it needs a bit more investigation, though I admit I can, and often am wrong about these things.

---

### Post by StuartN on 2009-12-16
> **thomashw said:**
> I have a lot of documents on my home desktop and would like to have them synced to my web space. I don't own the server so I can't install anything on it.

I have just been doing this, and obviously rsync can not write to an ftp server, and my ISP provides only ftp access.

The really easy solution is to Connect to Server under Places, then find that location under ~/.gvfs (the Gnome virtual filing system). You can then treat that just like any local directory and rsync to it, copy to it etc.

Incidentally, some applications (like Gedit) will seamlessly open, modify and re-save a document on ftp, which is great for a small edit.

---

### Post by thomashw on 2009-12-16
> **ajgreeny said:**
> Are you sure about that?  Surely if you can navigate to a specific folder on the server, you can also use rsync.  Perhaps it needs a bit more investigation, though I admit I can, and often am wrong about these things.
I don't think it's possible since I don't believe rsync supports FTP (like Stuart said.)

> **StuartN said:**
> I have just been doing this, and obviously rsync can not write to an ftp server, and my ISP provides only ftp access.

The really easy solution is to Connect to Server under Places, then find that location under ~/.gvfs (the Gnome virtual filing system). You can then treat that just like any local directory and rsync to it, copy to it etc.

Incidentally, some applications (like Gedit) will seamlessly open, modify and re-save a document on ftp, which is great for a small edit.
That's a good idea! I'll see if I can make that do what I want.

The Gedit FTP feature is awesome, btw. I used to use the same feature with Notepad++ when I used Windows - it's really convenient.

---

### Post by thomashw on 2009-12-16
So with rsync I understand I can mirror one directories contents (the "sender") to another directory (the "receiver"), but is it possible to mirror them both together?

Basically, have them both be senders/receivers so I can change either directory and see the changes in the other directory?

---

### Post by StuartN on 2009-12-17
> **thomashw said:**
> Basically, have them both be senders/receivers so I can change either directory and see the changes in the other directory?

In theory, you could run rsync desktop/ server/ and then run rsync server/ desktop/, which should send any new or updated files in both directions.

In practice, you may find that the ftp server redates all uploaded files with the upload time, so that rsync always sees the server files as updated. I don't know how well rsync handles time on a gvfs folder, and always assume the ftp site is the destination.

---

### Post by thomashw on 2009-12-17
I haven't looked into it too far, but I think Unison would be a better option for 2-way sync.

---

### Post by stinkeye on 2009-12-17
[_[COLOR="DarkRed"]luckyBackup[/COLOR]_]("http://luckybackup.sourceforge.net/") looks good.

---

### Post by thomashw on 2009-12-17
That does look good.

I wonder how they do the 2-way syncing with rsync. If I knew I could just implement it myself and skip using luckybackup.

---

### Post by stinkeye on 2009-12-17
Sorry, can't help with that.
I'm strictly a copy and paste man. :( :P

---

### Post by thomashw on 2009-12-17
No problem. :p

---

