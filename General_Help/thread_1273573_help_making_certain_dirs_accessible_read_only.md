---
title: "help making certain dirs accessible read only"
date: 2009-09-23
forum: General Help
---

### Post by strange. on 2009-09-23
hello guys i want to grant my friend access to my media folders /mnt/music and /mnt/movies by sshfs so he cant mount those dirs at his home to browse/play

how would i go about granting him access to those dirs only and read only so without him having access to any other place on my system and him not being able to modify any of the files in the dirs he does have access to?

thanks for any help

---

### Post by scragar on 2009-09-23
Create a new group:
```
sudo groupadd **musicShare**
```
Then add yourself and him to the group
```
sudo useradd -G **musicShare** $USER
sudo useradd -G **musicShare** **bob**
```
And finally make a public folder for the music where you own it, the group has read, but not write access to it:
```
sudo mkdir /opt/share
sudo chown -R $USER:**musicShare** /opt/share
chown -R 744 /opt/share
```Copy your music over and be sure to run those last to lines everytime you add to it to make sure he's no write perms on any new files(and that he has read perms :p)

---

### Post by strange. on 2009-09-23
is it possible without moving my data?
because i have the dirs in a place for my ftp etc and also moved over a few raids so i would prefer to share the folders in their current place

---

### Post by scragar on 2009-09-23
You could do it using symlinks I think.

---

### Post by strange. on 2009-09-23
wouldnt make the chmod 744 my files read only for everything then instead of just that single user

---

### Post by scragar on 2009-09-23
Use 740 then for the music directories.

---

### Post by strange. on 2009-09-23
so it is not possible to only set the permissions for this one person 
it has to be a "global" chmod?

---

### Post by scragar on 2009-09-23
Well, that's what the group is for, if you two are the only members of the group and the group owns the music then it's the group perms that apply and no-one else can access it.

---

### Post by strange. on 2009-09-23
what im trying to achieve is the opposite of that
make it allowed for everyone except the people in the group they should only have read access

---

### Post by strange. on 2009-09-24
bump

---

