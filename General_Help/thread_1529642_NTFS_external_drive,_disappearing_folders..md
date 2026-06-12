---
title: "NTFS external drive, disappearing folders."
date: 2010-07-12
forum: General Help
---

### Post by gvernold on 2010-07-12
I'm using an external hard drive formatted to NTFS to keep my projects on. I edit projects from both Ubuntu and Windows XP.

After editing some files in a couple of folders on the drive I have now noticed that any Ubuntu machine I plug the drive into can see the entire contents of the drive, but now, I have 4 folders that do not appear in Windows XP. I have plugged the drive backwards and forwards between three machines now (one of them dual boot) and Ubuntu definitely finds the folders and Windows definitely doesn't. This has only happened one Ubuntu has edited files, though some of the files and folders that have been edited are still visible in XP.

I presume something went wrong whilst writing file tables or whatever they are called these days. Does anybody know how I can get the folders visible in XP again? Do I need to run something in Ubuntu or in XP to 'rescan' the drive?

---

### Post by plypencil on 2010-07-12
I suggest using the checkdisk utility in windows to make sure there is not a file system error, if that does not find anything it is something Ubuntu has done to your drive and I do not have any suggestions.

---

### Post by chessnerd on 2010-07-12
Have you tried to show hidden files under Windows?

Under XP, open up Windows Explorer and go to the directory where the folders should be and go to Tools>Folder Options. Go to the View tab and select Show Hidden Files and Folders.

---

### Post by gvernold on 2010-07-12
Thanks, tried viewing the hidden files option but still can't see the folders. What I have discovered is that in Windows the file manager (explorer) cannot see them and neither can a couple of other Windows file managers that I have downloaded. Filezilla on Windows can see it and I tried to upload the files to my website and download them again to the drive, but unfortunately Windows still doesn't see them.

Checkdisk didn't find any errors on the drive either. This is really weird. It solves my problem but not why it occured in the first place but I will now move all the data off into Linux, reformat the drive a put the information back on. 

If anybody experiences the same thing please post back even though I seem to have some kind of solution. Thanks again.

---

