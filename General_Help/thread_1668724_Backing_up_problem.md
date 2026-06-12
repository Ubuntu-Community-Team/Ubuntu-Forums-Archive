---
title: "Backing up problem"
date: 2011-01-16
forum: General Help
---

### Post by SterlingM on 2011-01-16
I am trying to backup all of my files. I used the command - 
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys  
from this thread - 
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Eventually the backup process stops. The last two lines are -
/vmlinuz
tar: Exiting with failure status due to previous errors

I looked on Google, but couldn't find much of anything on this issue. Can anyone tell me what's wrong or how to go about backing it up a different way?

---

### Post by dFlyer on 2011-01-16
I think you need to use sudo if your backing up anything under /

---

### Post by dFlyer on 2011-01-16
I think you need to use sudo if your backing up anything under /

---

### Post by SterlingM on 2011-01-16
Well I am doing
sudo su
cd /

before that command...

---

### Post by Manyette on 2011-01-16
I am using the following command line to back up the entire machine, keeping in mind that it is not a "hard metal" backup.  For that you need to use Clonezilla or something similar:

tar -cvpzf /media/backup/lyric6.tgz --exclude=/media --exclude=/sys --exclude=/proc --exclude=/lost+found  --exclude=/tmp --exclude=/home/*/.gvfs /

This backs up to an external drive named "backup".  It has to be done either by preceeding it with sudo, or, as you said, sudo su and then cd /.  It has been working for me for a long time now.

---

### Post by Manyette on 2011-01-16
I am using the following command line to back up the entire machine, keeping in mind that it is not a "hard metal" backup.  For that you need to use Clonezilla or something similar:

tar -cvpzf /media/backup/lyric6.tgz --exclude=/media --exclude=/sys --exclude=/proc --exclude=/lost+found  --exclude=/tmp --exclude=/home/*/.gvfs /

This backs up to an external drive named "backup".  It has to be done either by preceeding it with sudo, or, as you said, sudo su and then cd /.  It has been working for me for a long time now.

---

