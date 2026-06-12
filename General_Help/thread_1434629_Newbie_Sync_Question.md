---
title: "Newbie Sync Question"
date: 2010-03-20
forum: General Help
---

### Post by Looking2learn on 2010-03-20
Hello, I am sure I have seen the script for this, but I can't seem to find it anywhere. 

 I have two Ubuntu boxes on the home network. One is being used as a backup computer, and the other an all purpose desktop. I have two external hard drives, one attached to each computer. 

 What I would like to do is compare a folder on the external hard drive attached to my desktop, with the external hard drive on the backup computer. Whatever files are on the desktop EXHDD, but not on the backup EXHDD, should be sent to the backup computer's EXHDD. 

 Sorry for the silly question, but everything I have found so far is to simply sync the folders, and not just adding to one. 

 I hope I have explained this ok. Thanks for any and all help.

---

### Post by asmoore82 on 2010-03-20
I would highly recommend Grsync.

It uses `rsync` as its backend which will compare file sets and bring them into sync.
for all of the gory details, see
```
man rsync
```

---

### Post by Looking2learn on 2010-03-20
Thank you very much, I'll look for it.

---

