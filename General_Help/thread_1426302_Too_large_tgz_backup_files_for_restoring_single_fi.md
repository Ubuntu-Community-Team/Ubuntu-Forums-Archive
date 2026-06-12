---
title: "Too large tgz backup files for restoring single files"
date: 2010-03-10
forum: General Help
---

### Post by parrimin on 2010-03-10
Hi, 

We are making backup for the server important folders into a external drive using tar and gzip. The source folder to backup is ~425GB. The problems are two:
- The result file is ~280GB, but when i do a du -sh of the external drive, it says the are ~425GB occupied. I can't understand the reason of that. I also tried to see the file size and disk occupied on a Windows system, and it says the same. So, what am I doing wrong?

- Another problem, and more important, is that when I have tried to recover some single files, the tgz file is so large that it take 1 day to list files. If I try to extract without listing, sometimes it says have not found the file, but I sure know that the file in inside. The problem is that on the folder to backup are some file/folder names with spaces and accents. Also this folders are accessed from Windows systems (samba), so the exact path of the file is difficult to know... Anybody can tell me if there is another better way to backup/restore?

---

### Post by Barriehie on 2010-03-10
I've also had issues with du reporting file sizes so can't help you there.  Have you explored perhaps using **rsync** to backup the folders/files?

---

### Post by parrimin on 2010-03-10
> **Barriehie said:**
> I've also had issues with du reporting file sizes so can't help you there.  Have you explored perhaps using **rsync** to backup the folders/files?

Thanks for reply so fast. Sorry, i have read something about rsync, but not used. So I thinks that's not the problem

---

### Post by Barriehie on 2010-03-10
> **parrimin said:**
> Thanks for reply so fast. Sorry, i have read something about rsync, but not used. So I thinks that's not the problem

With rsync you can get to the file(s) you have to restore much faster than a day.

---

### Post by parrimin on 2010-03-10
> **Barriehie said:**
> With rsync you can get to the file(s) you have to restore much faster than a day.

Hmm, reading more about rsync I can see it's... a great software. The only problem I can see is that synchronizing the result files are ~425GB, same as source. And... the external disk in connected via USB, so if going to make a backup without compressing, I could simply copy the entire directory I think, Could I?

But, I'm looking for rsync to make my own Dropbox XDD in home

---

### Post by Barriehie on 2010-03-10
> **parrimin said:**
> Hmm, reading more about rsync I can see it's... a great software. The only problem I can see is that synchronizing the result files are ~425GB, same as source. And... the external disk in connected via USB, so if going to make a backup without compressing, I could simply copy the entire directory I think, Could I?

But, I'm looking for rsync to make my own Dropbox XDD in home

rsync is faster than copying, I don't know how but it's quick! I don't know what Dropbox XDD is so you'll have to explain!

---

### Post by parrimin on 2010-03-10
> **Barriehie said:**
> rsync is faster than copying, I don't know how but it's quick! I don't know what Dropbox XDD is so you'll have to explain!

[https://www.dropbox.com/features](https://www.dropbox.com/features)

There is explained what Dropbox do. You have 2GB (in fact I have 3GB for friends inviting) free to sync between all the computers you install. I have installed on my house PC (Windows) and on my laptop (Ubuntu), and always have important files on Dropbox folders. You only have to copy the files you want to sync inside Dropbox folder, and automatically syncs. For example, i had my source code for university projects, and final project, and, saved my life, because the laptop crashed. And, if all computers crash, you can access to your account via web, and access the files.

I only can see advantages in this software... How can such a simple idea be so useful...

Of course you can make similar home things, but, this simply runs...

Thanks for your help already.

---

### Post by Barriehie on 2010-03-10
Cool idea, so what would be good would be just to setup a cron job that would sync the folders every so often or if handy in BASH AND source folder on ubuntu box then a daemon that would look for changes, via **inotifywait** and then start syncing every 20 min or whatever.  rsync can do just that, still would need either the daemon or the cron job.

Edit: 20 min. might be to fast for moving the amount of data you're involving!  But you get the idea, if the root folder changes, sync it.

---

### Post by Barriehie on 2010-03-14
So, how are you doing on this?

---

