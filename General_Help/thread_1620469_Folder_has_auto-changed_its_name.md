---
title: "Folder has auto-changed its name"
date: 2010-11-13
forum: General Help
---

### Post by azerty.123.450 on 2010-11-13
Hello, I'm on Lucid Lynx 10.4 and Gnome. 
I have a specific partition for my document, which is in the following folder /media/Documents
I don't know why a new folder /media/Documents_  has been created, and my files are in this one.
Now, files' permissions are the following :
```
drwx------ 2 root root  4096 2010-11-13 08:05 Documents
drwxrwxrwx 9 root root 20480 2010-11-13 11:04 Documents_

```

Is it not odd ?

---

### Post by WorMzy on 2010-11-13
After re-reading your post, the folder name hasn't changed at all. the "Documents" partition has just been mounted in a slightly different place, because it couldn't mount where it wanted to, for some reason.

Have you created an entry in /etc/fstab for this partition? Post it here if you have.

I'd unmount the partition
```
sudo umount /media/Documents_
```
then check that the /media/Documents folder is empty by running
```
sudo ls -a /media/Documents
```
and if it's empty, remove it with
```
sudo rmdir /media/Documents
```

After that, you should be able to remount the partition in it's usual place.

---

### Post by azerty.123.450 on 2010-11-15
Ok, thanks for your reply.

After a reboot, all return to normal.

Next time it will happened, I'll think about your answer.

++

---

