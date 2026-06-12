---
title: "Main user disappeared after changing UID and GID"
date: 2010-09-20
forum: General Help
---

### Post by hughessg on 2010-09-20
Problem: I run both Mac OS X and Lucid. I backed up my OS X partition in preparation for a restore. I also moved over important work documents to Lucid. Restored OS X using timemachine. Updated OS X with patches and moved over some files from external hard drive. After moving the files over, timemachine backed up system. I went into Time machine to transfer work documents over but the previous back up was deleted for the new one. I had the documents on Lucid. I just needed to switch it over to OS X. Therefore, I tried to enable read/write from Lucid to Mac OS X partition. I followed the steps outlined in [this]("http://ubuntuforums.org/showthread.php?p=1922676#post1922676") post.

Steps from post:
1. sudo usermod -u osx-uid ubuntu-username # change Ubuntu UID to 501
2. sudo umount /osx # UNMOUNT OSX PARTITION FIRST!!!
3. sudo find / -uid old-ubuntu-uid -print0 | xargs -0 chown osx-uid # change file permissions

OS X was unmounted prior to entering commands and performed the steps above under a different user. During step 3 I received an error stating you do not have sufficient privileges and the process stopped. I logged out of my temporary account and tried logging back into my main account. Main account was not present on the login screen. So I followed [these]("http://www.australianguy.com/2010/05/change-ubuntu-uid-to-501-for-os-x-file-access-simplified/") steps to change my UID and GID from 501 back to 1000. Login appeared. I tried to login but there was an error about ICEauthority and Nautilus. System doesn't load up and only shows wallpaper. I haven't deleted anything and I expect that I just need to point my UID back to wherever my home folder is. Any help would be appreciated. Thanks in advance...

---

### Post by CharlesA on 2010-09-20
What UID was the OSX user listed as?

If you have the same UID between installs, you don't have to change the permissions (thankfully).

---

### Post by hughessg on 2010-09-20
501...I don't care about writing to OS X anymore. I just want to get my home directory back in Ubuntu.

---

