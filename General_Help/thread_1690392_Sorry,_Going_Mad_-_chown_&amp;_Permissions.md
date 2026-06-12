---
title: "Sorry, Going Mad - chown &amp; Permissions"
date: 2011-02-18
forum: General Help
---

### Post by Quarkrad on 2011-02-18
Sorry but I'm going round in circles.  I have been playing around backing up firefox on my laptop (and for friends who I have converted to Ubuntu) in case of laptop melt down.  I have been backing up the ./Mozilla into Dropbox so I have an easy backup environment for my/friends laptop. To test I remove firefox from my laptop via Synaptic and delete the ./Mozilla folder from Home.   I download the backup ./Mozilla folder from Dropbox and install a clean version of firefox.  I copy the contents of the backed up ./Mozilla folder into the new ./Mozilla folder in Home.  There are a number issues including the profile name but one of the main issues is that the owner of all the folders and files in the backed up ./Mozilla folder becomes **root**.  I have been trying 'global' change commands in terminal on ./Mozilla rather than via gksudo nautilus.  My user name is **dad** - what command do I enter in terminal in order to change the ownership and permissions of any folder and file in ./Mozilla to **dad** and **read/write**?

---

### Post by 3Miro on 2011-02-18
1. Unix uses case sensitive file system, meaning .mozilla and .Mozalla are two different folders.

2. You should not copy the old .mozilla over the the new one, instead you should remove the old .mozilla (delete it) and put the new one on its place (otherwise you merge the two folders and get in trouble with the profile names).

3. To change the ownership of all files in a given folder (including all of the sub-folders) use:
```
sudo chown -R newuser:newgroup some_folder
```
-R means recursively apply to all sub-folders, newuser and newgroup should be dad:dad in your case i.e:
```
sudo chown -R dad:dad /home/dad/.mozilla
```

The command is typed into the Terminal (Apps -> Accessories -> Terminal).

---

### Post by oldfred on 2011-02-18
If dropbox is NTFS you lost both ownership and permissions.

3Miro has the ownership issue covered.

If you need permissions corrected:

Correct permissions:
chmod -R 755 ~/.mozilla

---

### Post by The Cog on 2011-02-18
To retain the file ownership and permissions, you could (as root) use "cp -a" which does and archiving type copy. But as oldfred says, copyiong to NTFS will always lose the premissions etc. So it you're copying to NTFS, it would be better to use tar to create a tar file which is like a zip file but also stores the unix file attributes.
> tar cf mozbackup.tar .mozilla

---

