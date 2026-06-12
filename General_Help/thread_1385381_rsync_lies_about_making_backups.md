---
title: "rsync lies about making backups"
date: 2010-01-19
forum: General Help
---

### Post by HyperHacker on 2010-01-19
For a while I've been using rsync to back up:
sudo rsync -avHEAXxh --inplace --delete --exclude=/home/hyperhacker/video --progress --log-file=/home/hyperhacker/video/.backup.log /home/hyperhacker /home/hyperhacker/video/.backup/home

A few months back I noticed it was backing up some files every time, even though they hadn't changed. Today I discover that although it's been reporting normally and listing the proper set of files backed up every night, it hasn't actually backed anything up since about Jan 3. Needless to say the loss of over two weeks of work is more than a little annoying.

---

