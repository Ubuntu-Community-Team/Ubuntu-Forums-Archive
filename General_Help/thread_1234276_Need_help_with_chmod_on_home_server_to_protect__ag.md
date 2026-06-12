---
title: "Need help with chmod on home server to protect  against WinXP vulnerability"
date: 2009-08-07
forum: General Help
---

### Post by flatland2d on 2009-08-07
I am planning to build a home server and I've been doing tests with my laptop acting as a server to get an idea how how it's going to work.  The server (Ubuntu) will need to share folders with other machines, including WinXP.  The server will have two 1TB drives rsync'ed together for backups.  My worry is a potential virus on WinXP could destroy the shared folder on the server, which would also destroy the backup drive the next time rsync runs, if not caught in time.  So my issue is, I need a way to allow WinXP to create new files, but not edit or delete existing files.

In theory, I think I can accomplish this by running a cronjob to automatically set permissions at regular intervals.  When the files are copied over from WinXP (ntfs), they have no ownership or permissions.  I can chown and chmod 644 to block WinXP from making further changes to the file.  So this should allow WinXP to create files, but will block changing files after the next cronjob.

That much I have done already, but it's not working the way I want it to.

In order for WinXP to be able to copy and paste files to the server, I need to set the share folder to read and write access for everyone.  The individual files are then set with:

cronjob: 
```
* * * * * Documents/script.sh
```
In reality I will not be running this once a minute.  It's just for testing.

script.sh
```

#!/bin/bash

echo "Backup initiated by script on" $(date) >> backup-testing/backup.log
sudo /bin/chown ryan backup-testing/*
chmod 644 backup-testing/*
rsync -av backup-testing/ backup-store/
```
I have added my user to sudoers file to allow the script to run chown without a password.  The folder backup-testing/ is shared with WinXP

The problem is, I can save over and delete files in backup-testing/ from WinXP.  I can open a picture in Photoshop and save back to the same file without being blocked (a file that is set to 644).  I'm thinking this may have something to do with the share options for the folder, since it is set to global read and write access.  If I set the shared folder to 644, I can block saving and deleting from WinXP, but I can't save under a different name or create a new file in the folder.

So basically, I want a way that I can drag and drop pictures straight from my camera from WinXP to the shared folder, with the permissions to create new files, but not edit or delete existing files.  What am I doing wrong or how can this be done?  Is there a better way? (and please don't say stop using Windows - it's our main family computer and my wife won't make the switch #-o)

---

### Post by flatland2d on 2009-08-10
Any help?  I need to have permissions to allow new files to be created, but disallow existing files to be written to or deleted.

I'm wondering if this wasn't working because Photoshop and Word create temporary files when you open a file?

---

### Post by hpark21 on 2009-08-10
Perhaps cron job to move any files that gets dropped at a location to alternate location WITHOUT write access?  (only read access)

So, you will have 2 shares:
Share A (full access) where files gets dropped
Share B (read only access) where the files gets moved periodically (every 5 minutes? )

---

### Post by asmoore82 on 2009-08-10
It's quite a pickle! Creating and deleting file go hand in hand -
both controlled by write access to the parent folder.
The exception is for "sticky" folders, setting the "sticky" bit on a folder
will allow files to be deleted only by those who have write permission on the
folder *and* those files, or by the owner of the entire sticky folder itself.

This will set a folder as sticky with read/write access to everyone,
but only the owner of a file or the folder will be allowed to delete it:
```
chmod 1777 "*Public Folder*"
```

On the bright side, rsync will not delete files from the destination
unless it is explicitly given the `--delete` option.

---

### Post by flatland2d on 2009-08-10
> **hpark21 said:**
> Perhaps cron job to move any files that gets dropped at a location to alternate location WITHOUT write access?  (only read access)

So, you will have 2 shares:
Share A (full access) where files gets dropped
Share B (read only access) where the files gets moved periodically (every 5 minutes? )

Something like this has crossed my mind, but it still has a problem in that it won't support nested folders.  Say I want to copy and paste a bunch of pictures to be added to an existing sub-directory - it won't be able to do that.  Everything will end up in the same directory that the cronjob writes to.

---

### Post by flatland2d on 2009-08-10
> **asmoore82 said:**
> It's quite a pickle! Creating and deleting file go hand in hand -
both controlled by write access to the parent folder.
The exception is for "sticky" folders, setting the "sticky" bit on a folder
will allow files to be deleted only by those who have write permission on the
folder *and* those files, or by the owner of the entire sticky folder itself.

This will set a folder as sticky with read/write access to everyone,
but only the owner of a file or the folder will be allowed to delete it:
```
chmod 1777 "*Public Folder*"
```

On the bright side, rsync will not delete files from the destination
unless it is explicitly given the `--delete` option.

The sticky bit sounds pretty close to what I want to do.  I'll have to play around with it some tonight.

What is the difference between Word being able to save an existing file on the server it doesn't have permissions to (644) and Notepad not being able to save the file.  Notepad does what I expect it to, but not Word (and I'm guessing any other program that opens a temp file).  The folder for this example is set to 666.

Taking a step back, how much of this is a reasonable precaution to guard against a virus on a remote machine?  Will permissions really help, or will the virus be able to overflow into other parts of the server by writing a long string of garbage?  I don't know enough about how viruses work to really know.  What can be done here?

I'm wondering if maybe I shouldn't automate the rsync command, so that way I can be sitting in front of the computer, making sure everything looks good before backing up.  Not nearly as convenient though.

Thanks a bunch for the input.

---

