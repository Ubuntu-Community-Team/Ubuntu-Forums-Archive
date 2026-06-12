---
title: "tar command line questions"
date: 2012-01-14
forum: General Help
---

### Post by suffer1989 on 2012-01-14
im currently on a plop linux live CD, and im trying to backup my old home folder from my old ubuntu installation using tar.

I had the original parition  "/dev/sda1" and I mounted it into a new folder "/mnt/ubuntu". I also mounted the backup partition "dev/sda4" to "/mnt/backup'

Then I cd to the backup directory "/mnt/backup" in terminal, and tried out 
```
tar -cvpzf backup.tar.gz /mnt/ubuntu/home/[username]/test.directory/
```

Everything turned out hunkydory, except, when I opened the archive "backup.tar.gz", it started from the "mnt" directory, as opposed to simply the test folder.

My question is : How can I specify tar to "begin" the archive, at a certain point ? 
EG, make a tar of a directory inside my user-folder, and the resulting archive opens from there, as opposed to "mnt>ubuntu>home>[username]>specified folder"

also, if I want to exclude all hidden files in that directory, I assume I need to put ```
--exclude .*
``` after ```
tar -cvpzf backup.tar.gz /mnt/ubuntu/home/[username]/test.directory/
```
 ?

---

### Post by suffer1989 on 2012-01-14
Bump ? Anybody ? : (

---

### Post by suffer1989 on 2012-01-14
resolved here : 
[http://www.linuxquestions.org/questions/showthread.php?p=4574745](http://www.linuxquestions.org/questions/showthread.php?p=4574745)

---

### Post by Habitual on 2012-01-15
Props for self-reliance and finding an answer.

---

### Post by Double.J on 2012-01-15
N.B. you actually stumbled on the key reason we use tar for back ups instead of g/b zip without tar- because it preserves ownership ;)

---

