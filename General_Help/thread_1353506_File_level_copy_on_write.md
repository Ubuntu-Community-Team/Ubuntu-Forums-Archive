---
title: "File level copy on write?"
date: 2009-12-12
forum: General Help
---

### Post by nerdopolis on 2009-12-12
Hi. are the any utilities out there that I can use to set up whenever a file or folder, within a particular directory is created/modified, the changes also get instantly copied over to another folder? If it created file4 in Folder1, to copy it over to RedirectFolder?

Example of folder contents:
Folder1                       
file1
file2

RedirectFolder
file3

If so, can it foward deletes? if it tries to delete file3 in Folder1, it fails, but it succeeds in RedirectFolder?

I do not what the contents of RedirectFolder to appear in Folder1, so I can't use AUFS.

---

### Post by nerdopolis on 2009-12-14
Are there any such programs?

---

### Post by lavinog on 2009-12-14
I think rsync has a way to monitor for changes.

---

### Post by lavinog on 2009-12-14
here is a howto:
[HOWTO: make your machine react to changes in a directory](http://ubuntuforums.org/showthread.php?t=1104716)

---

### Post by nerdopolis on 2009-12-14
Thanks for the tip.

But whats not clear in the how to is can it forward deletes?

Example of folder contents:
Folder1                       
file1
file2

RedirectFolder
file3

for example if I was to try to delete file3 in Folder1, will it be able to pick that up so it can delete file3 in RedirectFolder?

---

### Post by lavinog on 2009-12-14
I think you are supposed to use the script to call rsync which will syncronize the folder (use the -delete option)
I have never had a need for such a script, so I have not tried it personally.

---

### Post by nerdopolis on 2009-12-14
Thanks for your suggestion for the Python script, and your time.


I thought it through a little more and I might be able find some hacks for the deletion issue. 

Thanks again.

---

### Post by llamabr on 2009-12-14
> **nerdopolis said:**
> Thanks for your suggestion for the Python script, and your time.


I thought it through a little more and I might be able find some hacks for the deletion issue. 

Thanks again.

I can't quite figure out why you want to do this, so I'm not sure what the problem is.  but rsync will syncronise two folders, including deleting a file from one when you delete it from another.  You don't want files forwarded (whatever that even means) you want directories syncronized.  That's the job of rsync.

---

### Post by todak on 2009-12-14
I use **Back In Time** (**backintime** as it is referred to in the repos). It is a GUI for rsync and it works quite well. It is MY preference for syncing my files and folders to an external drive. If you delete a file, then its deletion will be mirrored in the backup directory you created. It is a really nice app.

Edit: I missed the "instantly" part! Apologies.

---

### Post by lavinog on 2009-12-15
I think the op wants this to happen automatically without user interaction.
a while loop could be used, but it would be a waste of resources

---

### Post by nerdopolis on 2009-12-29
Thanks for your help. Unfortunately I wanted Copy on Write for a work around, but the work around itself failed. 

Thanks though. If I need this again, I know where to look.

---

### Post by dcstar on 2009-12-30
> **nerdopolis said:**
> Hi. are the any utilities out there that I can use to set up whenever a file or folder, within a particular directory is created/modified, the changes also get instantly copied over to another folder? If it created file4 in Folder1, to copy it over to RedirectFolder?

Example of folder contents:
Folder1                       
file1
file2

RedirectFolder
file3

If so, can it foward deletes? if it tries to delete file3 in Folder1, it fails, but it succeeds in RedirectFolder?

I do not what the contents of RedirectFolder to appear in Folder1, so I can't use AUFS.

fam fileschanged

[http://ubuntuforums.org/showthread.php?t=89773](http://ubuntuforums.org/showthread.php?t=89773)

---

