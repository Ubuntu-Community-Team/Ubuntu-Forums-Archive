---
title: "sshfs + gedit can't save file"
date: 2010-11-18
forum: General Help
---

### Post by Yappix on 2010-11-18
I mounted a remote directory using sshfs and I can't save files using gedit, while saving same file using vi works. Changin permission to o-r (640) allows gedit to save files OK. Is there a way to change sshfs connection to make gedit work without chmodding every file? (I use -o uid=`id -u` -o gid=`id -g`, so that remote files seem to be owned by me)

```
$ touch test.txt 
[!] test.txt appears

$ vi test.txt 
[!] :wq -> saves just FINE

$ gedit test.txt 
[!] opens fine, but upon save shows "You do not have the 
[!] permissions necessary to save the file" error - 
[!] CAN'T SAVE

$ vi test.txt 
[!] edit, :wq -> again saves just FINE!

$ ls -l test.txt
-rw-r--r-- ..... test.txt

[!] Now the tricky part:

$ chmod o-r test.txt
-rw-r----- ..... test.txt  <-- removed 'read' perm. from 'others'
$ gedit test.txt 
# WORKS! Saves just fine! 
```

Why removing read permission from others allows gedit to save? (while vi and the rest doesn't have that problem?)

Is there a way to change sshfs connection string to allow me to edit all files directly on server, without having to chmod o-r them?

---

### Post by Yappix on 2010-11-18
-o workaround=rename 
solved the problem

---

### Post by mrule on 2011-04-20
this did not solve the problem for me.

---

### Post by mrule on 2011-04-20
the chmod workaround also does not work for me.

---

### Post by daniel_ba on 2011-07-26
Just for the record, you should add the workaround to the sshfs statement. 

eg. sshfs -o idmap=user,workaround=rename $USER@host:/project /home/$USER/project

This worked for me, thanks Yappix.

---

