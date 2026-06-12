---
title: "Why doesn't Trash work (ext3)"
date: 2010-09-23
forum: General Help
---

### Post by UncleBoarder on 2010-09-23
I formated a second drive as ext3.  Shouldn't I be able to use the GUI trash?  I get an error that they must be deleted immediately.


# My shared volume /dev/sdb1 (show it on desktop)
UUID=e0352916-43a0-431c-bd64-08a5f3182543  /media/data            ext3  rw    0  0

In another thread, someone suggested using "user" in fstab but that defaults to noexec.  I don't want to be limited from executing programs.

This must have worked in previous versions when ext3 was the latest/greatest right?

Yes I could go to ext4... but do I have to?  Shouldn't this work?

---

### Post by drs305 on 2010-09-23
You can have more than one option in the fstab line - i.e. I can have *users* and *exec* if I choose. I have a *mytest* mount point, which I own, and to which I mount an ext3 partition which I labeled  "test":
> LABEL=test /mnt/mytest ext3 defaults,users,exec 0 2

When I delete something from this folder it is moved to my normal trash bin.

---

### Post by UncleBoarder on 2010-09-24
Armed with the knowledge that it SHOULD work, I began from scratch.

Reformat the volume as ext3 - yes I can use the Trash
Add my files and create an appropriate fstab entry - yes I can still use the Trash
Add fstab entry to move my /usr/local directory to the ext3 volume - yes I can still use the Trash
Add fstab entry to move my /home directory to the ext3 volume...
[B]
No.  Trash is now broken.  Why?[/B][FONT=Fixedsys]
[/FONT][INDENT]# My shared volume /dev/sdb1 (show it on desktop)
UUID=a726a583-03e5-47c6-9618-ddbfcdd4c1d6        /media/data              ext3  defaults,users,exec    0  0

# Moving /usr/local
/media/data/Ubuntu/usr/local                     /usr/local               bind  defaults,bind           0  0

# Moving /home
/media/data/Ubuntu/home                          /home                    bind  defaults,bind        0  0  

[/INDENT]I tried the bind entries both with "users,exec" and without.

---

### Post by UncleBoarder on 2010-09-25
I tried duplicating the new volume home directory and changing the owner to root:root instead of me.  It caused an error at boot but it did boot.  And when I tried to delete a file, it gave me a little more info.  This is not my goal, I'm just changing stuff trying to determine why I can't delete to Trash.  I think this might be a clue...

It said "unable to create trash info file: permissions".

I then looked at a correctly functioning .Trash-1000 directory and found it's owned by the user and there's an info subdirectory that contains the recently deleted files with a new extension added... named....

.trashinfo

So it appears this is somehow a permissions issue but since I'm logged on as me, and the file system is owned by me, and the permissions say the owner as rw rights... wtf?!?

I don't understand.

Does anyone understand how Trash works?

Or are there any tools that show me what Ubuntu is attempting in the background when I delete a file?

---

### Post by asmoore82 on 2010-09-26
> **UncleBoarder said:**
> Does anyone understand how Trash works?

When you delete something from your home folder, it gets moved to your private trash folder.
This used to be "~/.Trash/"  but is now "~/.local/share/Trash/"

Now I'm not 100% sure, but deleting something from an external drive is different.
It gets moved to a public trash folder at the root level of the drive.
It is also tagged with your User ID number, which will always be 1000 for the primary account on an Ubuntu system.

---

### Post by ankspo71 on 2010-09-26
Hi,
Maybe these links might be of some help?
1 [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
2 [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you 'copied' the home folder, then I think what could have happened is that some of the files in your home folder didn't retain their permissions settings (or copy completely skipped some files) when they were being transferred over to the new partition. 

Link 2 says:
> Rsync is designed for backups of /home, and much more. It is able to maintain other characteristics of the file, like permissions, ownership, and timestamps. There was a lot of debate about which command to copy your files to the new /home partition which stemmed from a time when cp was not able to do it properly (apparently it skipped files?). Cp was not designed to be a powerful backup tool, rsync was. The fix, then, was to use a combination of find and cpio
...
Rsync was chosen over cp and find|cpio because it seemed to maintain permissions. 

Hope this helps.

---

### Post by UncleBoarder on 2010-09-26
The first time I copied my home directory to my second volume I used...[INDENT] $find . -depth -print0 | cpio --null --sparse -pvd /media/data/Ubuntu/home
[/INDENT][FONT=Verdana] I just tried your rsync method...[/FONT][INDENT] sudo rsync -axS --exclude='/*/.gvfs' /home/. /media/data/Ubuntu/home/.
[/INDENT][FONT=Verdana]They both appear to work the same.  Meaning I still have the problem and can not use the Trash when /home is moved to the second volume.  I'm forced to either delete immediately or skip the deletion.

[/FONT][FONT=Verdana]I found a site that mentioned problems when the trash is on a different volume than the file being deleted.  That is not the case here but is it possible Ubuntu becomes confused when the /home directory is moved?[/FONT]

Recall that I successfully moved the /usr/local directory... so I don't know.  How is /home causing this problem?

I'm still looking for an answer.

---

### Post by concord on 2010-09-27
> **UncleBoarder said:**
> 
Add fstab entry to move my /home directory to the ext3 volume...
[B]
No.  Trash is now broken.  Why?[/B][FONT=Fixedsys]
[/FONT][INDENT]# My shared volume /dev/sdb1 (show it on desktop)
UUID=a726a583-03e5-47c6-9618-ddbfcdd4c1d6        /media/data              ext3  defaults,users,exec    0  0

# Moving /usr/local
/media/data/Ubuntu/usr/local                     /usr/local               bind  defaults,bind           0  0

# Moving /home
/media/data/Ubuntu/home                          /home                    bind  defaults,bind        0  0  

[/INDENT]I tried the bind entries both with "users,exec" and without.

Did you update your /etc/passwd file to let the system know your home directory is now located at '/media/data/Ubuntu/home' ?

---

### Post by UncleBoarder on 2010-09-28
Awesome!  It works!!

It's a different path to the trash but it works!

Old path is /media/data/.Trash-1000

New path is /media/data/Ubuntu/home/ed/.local/share/Trash

Thanks!!!!

---

