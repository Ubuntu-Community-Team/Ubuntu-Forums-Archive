---
title: "why don't I have to exit an app when upgrading?"
date: 2012-04-27
forum: General Help
---

### Post by PGScooter on 2012-04-27
This is just a question out of curiosity. How am I able to keep using applications when I upgrade them? Is it because they are loaded into RAM so that deleted the system files doesn't matter? Does this depend on whether the application calls external scripts/libraries (say, in the same folder)?

Thanks

---

### Post by dino99 on 2012-04-27
Thats right , working app is loaded into ram so updating on hdd is possible  :guitar:

---

### Post by imachavel on 2012-04-27
yes but this can cause confliction errors. It's always best to close all your aps when upgrading. Also, it doesn't delete your app, it updates system files, then deletes old versions, so the new files are written in first. Your app won't be deleted unless it's upgraded with the OS, either way your file needs to close when the OS restarts for upgrade to complete.
 
Btw, my upgrade completely failed, which I should have expected like a billion peoples upgrades failed today. I am trying to go through this to fix it:
 
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)
 
but it won't even open update manager. A fresh install would be best? Really can I revert to a previous kernel? I believe I can it seems to be grub option

---

### Post by imachavel on 2012-04-27
> **PGScooter said:**
>  Does this depend on whether the application calls external scripts/libraries (say, in the same folder)?
 
Thanks
 
well yes. Of course it would. Like I said when it starts cleaning up old files it's best to have the app closed, it can really cause problems writing when the apps are open during upgrade anyway. Good question though, and solid understanding.

---

### Post by PGScooter on 2012-04-27
ok thanks

---

### Post by 3rdalbum on 2012-04-27
Make a copy of a video file. Start playing the copy. While playing, delete the copy. You'll notice it is still playing.

That's because Linux delays the deletion of files that are already open. To everything on the system, the file has been deleted - EXCEPT for the program that still has the file open.

Still not a great idea to run programs while they are being updated, in case they try to call on a file that was not open and has now been updated. The program might encounter a mismatch of versions and crash. However I've not had a problem.

I've even seen a video of somebody erasing every file on their hard disk while Ubuntu has been running from that disk. The system stays running even after everything is deleted.

---

### Post by PGScooter on 2012-04-27
> **3rdalbum said:**
> Make a copy of a video file. Start playing the copy. While playing, delete the copy. You'll notice it is still playing.

That's because Linux delays the deletion of files that are already open. To everything on the system, the file has been deleted - EXCEPT for the program that still has the file open.

Still not a great idea to run programs while they are being updated, in case they try to call on a file that was not open and has now been updated. The program might encounter a mismatch of versions and crash. However I've not had a problem.

I've even seen a video of somebody erasing every file on their hard disk while Ubuntu has been running from that disk. The system stays running even after everything is deleted.

Ah, I thought it was just that the video was loaded into RAM. That's not the case?

---

