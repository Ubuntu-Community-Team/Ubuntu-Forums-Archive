---
title: "time format problem in ubuntu10"
date: 2010-09-08
forum: General Help
---

### Post by amwamw968 on 2010-09-08
hi,
    when i used command like this in ubuntu 10.04&#65306;
 
      stat file1 
 
  and display show like this&#65306;
 
  File: “file1”
  Size: 0               Blocks: 0          IO Block: 4096   
Device: 801h/2049d      Inode: 3350638     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/   amw)   Gid: (    0/   amw)
Access: 2010-09-03 16:00:54.[COLOR=red]652302345[/COLOR] +0800
Modify: 2010-08-23 09:03:53.[COLOR=red]652302345[/COLOR] +0800
Change: 2010-08-23 09:03:53.[COLOR=red]652302345[/COLOR] +0800
 
 
but the same command in Redhat Ent 5 show in different result&#65306;
 
  File: “ssh-rsa”
  Size: 0               Blocks: 0          IO Block: 4096   
Device: 801h/2049d      Inode: 3350638     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    amw)   Gid: (    0/    amw)
Access: 2010-09-03 16:00:54[COLOR=red].000000000[/COLOR] +0800
Modify: 2010-08-23 09:03:53.[COLOR=red]000000000[/COLOR] +0800
Change: 2010-08-23 09:03:53.[COLOR=red]000000000[/COLOR] +0800
 
 
i mean &#65292; file‘s Access/Modify/Change   time  format show in different way &#65292; 
ubuntu is “[COLOR=red]16:00:54.652302345[/COLOR] ” &#65292;
redhat is “[COLOR=red]16:00:54.000000000[/COLOR] ”&#12290;
when i compile some application in ubuntu 10&#65292;  this will cause automake again&#12290;
can anybody tell me how to change this features &#65311; i don't want a float time format&#12290;
 
thanks&#65281;

---

### Post by dcstar on 2010-09-09
> **amwamw968 said:**
> hi,
    when i used command like this in ubuntu 10.04&#65306;
 
      stat file1 
 
  and display show like this&#65306;
 
  File: “file1”
  Size: 0               Blocks: 0          IO Block: 4096   
Device: 801h/2049d      Inode: 3350638     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/   amw)   Gid: (    0/   amw)
Access: 2010-09-03 16:00:54.[COLOR=red]652302345[/COLOR] +0800
Modify: 2010-08-23 09:03:53.[COLOR=red]652302345[/COLOR] +0800
Change: 2010-08-23 09:03:53.[COLOR=red]652302345[/COLOR] +0800
 
 
but the same command in Redhat Ent 5 show in different result&#65306;
 
  File: “ssh-rsa”
  Size: 0               Blocks: 0          IO Block: 4096   
Device: 801h/2049d      Inode: 3350638     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    amw)   Gid: (    0/    amw)
Access: 2010-09-03 16:00:54[COLOR=red].000000000[/COLOR] +0800
Modify: 2010-08-23 09:03:53.[COLOR=red]000000000[/COLOR] +0800
Change: 2010-08-23 09:03:53.[COLOR=red]000000000[/COLOR] +0800
 
 
i mean &#65292; file‘s Access/Modify/Change   time  format show in different way &#65292; 
ubuntu is “[COLOR=red]16:00:54.652302345[/COLOR] ” &#65292;
redhat is “[COLOR=red]16:00:54.000000000[/COLOR] ”&#12290;
when i compile some application in ubuntu 10&#65292;  this will cause automake again&#12290;
can anybody tell me how to change this features &#65311; i don't want a float time format&#12290;
 
thanks&#65281;

Use the same filesystem.

---

### Post by amwamw968 on 2010-09-09
thanks for  helping me

---

