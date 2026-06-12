---
title: "sshfs problem"
date: 2009-11-11
forum: General Help
---

### Post by Cardale on 2009-11-11
I am trying to mount a local lan drive and it worked perfectly the first time now I am getting some werid errors

I can mount the drive I want no problem, but I don't have permissions.  How can I grant root permissions?

Why am I getting this as well?
d????????? ? ?    ?       ?                ? game
d????????? ? ?    ?       ?                ? laptop

---

### Post by Cardale on 2009-11-11
bump

---

### Post by tuwe on 2009-11-11
> **Cardale said:**
> bump the forum is not a chat.

can you please give some details about which commands you use to mount and where you put them.

---

### Post by Cardale on 2009-11-11
I have gotten everything working my Ubuntu Server is connecting to my XP machine running cygwin and mounting the drive using sshfs, but I am not getting the permissions I need.

drwx------ 1 1006  513    0 2009-11-10 17:23 game

```
sudo sshfs -o nonempty,allow_other,default_permissions username@ip:C:/ /media/game
```

Then I enter my password and it mounts.

---

### Post by Cardale on 2009-11-11
bump

---

### Post by Cardale on 2009-11-12
bump bump

The envornment is Ubuntu Server acting as client to a Cygwin Game server that runs XP.  I found that the userid are different and was told this would affect it, but how can I change the userid on the cygwin system to 1000?

---

### Post by Cardale on 2009-11-12
for the love of god!! 

bump :D

---

### Post by Cardale on 2009-11-14
bump

---

### Post by Cardale on 2009-11-14
bump

---

### Post by Portable_Jim on 2009-12-13
> **Cardale said:**
> I have gotten everything working my Ubuntu Server is connecting to my XP machine running cygwin and mounting the drive using sshfs, but I am not getting the permissions I need.

drwx------ 1 1006  513    0 2009-11-10 17:23 game

```
sudo sshfs -o nonempty,allow_other,default_permissions username@ip:C:/ /media/game
```Then I enter my password and it mounts.
You have used "sudo sshfs..." which means that only root can read the folder (hence the funny permissions on the folder). However, if you do not use sudo, it will fail.

Catch 22? No. You need to change the permissions of the folder.
Try
```
sudo chown local_user /media/game
```to make the folder owned by you.

Then
```
sudo chmod 755 /media/game
```so other users can view the file (optional). For more information about permissions, see [http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html).

Now we can mount the sshfs share:
```
sshfs -o nonempty,allow_other,default_permissions username@ip:C:/ /media/game
```

---

