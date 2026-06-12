---
title: "tar backup question"
date: 2010-04-12
forum: General Help
---

### Post by nmobrien4 on 2010-04-12
So I've been researching ways to make a complete backups of my partition (I like to mess around in the terminal) but before I try anything I just wanted to make sure of what exactly would happen if say I did this:

```
tar cvzpf /home/backup.tgz --same-owner --exclude=/home/backup.tgz --exclude=/home/error.log --exclude=/proc/* --exclude=/media/* --exclude=/dev/* --exclude=/mnt/* --exclude=/sys/* --exclude=/tmp/* /
```then moved the file to another computer with ubuntu 9.10 installed and restored using:

```
sudo tar xvzf /home/Backup.tgz -C /
```I am not completely new to linux but it has been a while since I've used it. Any input would be appreciated.

EDIT: Oh and also, whenever I try to restore a file I get the error message "tar: [name of file]: Not found in archive"

---

### Post by labinnsw on 2010-04-18
I would change the name of the back up. Other than that it looks good. Just in case I missed anything, here is a link to [the instructions I use regularly]("http://ubuntuforums.org/attachment.php?attachmentid=144765&d=1264321402")

---

