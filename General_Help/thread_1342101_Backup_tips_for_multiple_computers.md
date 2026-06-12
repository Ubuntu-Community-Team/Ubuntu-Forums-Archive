---
title: "Backup tips for multiple computers"
date: 2009-11-30
forum: General Help
---

### Post by Valir on 2009-11-30
Hey, 

does anyone have tips or advice on how to best set up an intelligent backup system?

I have two computers and one external hard drive, and would like to

1. Backup Music and Pictures from both computers into a Shared folder on backup-drive.

2. Backup home folders (except music&Pictures) for each comp to separate folders on backup-drive

3. Have it real simple and gnomy with automatic notification (my gf uses the other comp)

.....

I know there a lot of apps out there: Back in time, Keep and a sync utility in gnome-commander for file management, and rsync; but would like to know the best set up so I woldn't screw something up without understanding what goes where. 

Has anyone set up the perfect scheme for something like this?

Would be grateful to hear some tips on how you did it,

cheers! :popcorn:

P.s. In the case of backing-up Pics and Music to one shared folder, the shared folder would hold most of the music and pics, but NEW would be synced/added from each computer. (I mean to say, if something is deleted on the computers it would not be deleted from the backed-up folder through some sync feature)

P.s.s. But in the case of backing-up Home folders separately, modified and new files would be synced.

P.s.s.s. Would you use one backup system? Or one backup apps for the purpose of backing up documents on Home folders, and some syncing feature in some Pic and music apps? (I know something like it would be possible through Songbird, but what about pics? F-spot?)

---

### Post by fluffman86 on 2009-11-30
rsync -avzu /from/folder /to/usb/drive/folder

a = archive mode (recursive, maintain permissions)
v = verbose, show what's going on
z = compress (hopefully faster)
u = update, only change the bits that have changed.

---

### Post by StuartN on 2009-11-30
> **fluffman86 said:**
> z = compress (hopefully faster)

I wouldn't use compression (assuming there is enough space) because it makes the backup slightly less accessible, rather than a useable duplicate.

You can occasionally snapshot the rsync backup, without using any extra space, by creating hardlinks. This guide explains one easy method: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/) - it is what back-in-time does.

You also need to be aware of users and permissions. The user id number (not the user name) must match between your two computers. You can cheat by using NTFS and assigning ownership at mount time, or use sudo -u <fileowner> for ext filesystems.

---

### Post by akakingess on 2009-11-30
I have used grsync (just the GUI version of rsync) and have loved it, although I have not done with multiple computers, I have not crossed that bridge yet, so you would have to let me know how it goes if you go that route, so please keep me informed as to your progress and good luck and I hope you find the perfect app for your uses.

---

### Post by XCan on 2009-11-30
> **StuartN said:**
> I wouldn't use compression (assuming there is enough space) because it makes the backup slightly less accessible, rather than a useable duplicate.


Actually, the -z flag only uses the gzip algorithm during transfer. It doesn't store the files compressed. :)

---

