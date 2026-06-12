---
title: "user www-admin: cannot change permissions"
date: 2010-01-03
forum: General Help
---

### Post by amalgamas on 2010-01-03
I run a win exe under wine/ubuntu Karmic that needs to access and write to files owned by user 'www-admin'.  Group permissions are read only.  I have joined the grup 'www-admin', but I cannot find a way to change group permissions to rwx or to change owner to achieve this.  I have tried this as user 'www-admin', and I have edited /etc/sudoers with the line:
www-data ALL=(ALL) NOPASSWD:ALL so the password problem is solved.  Nothing helps.  Can someone give me a hint?

---

### Post by konqueror7 on 2010-01-03
> **amalgamas said:**
> I run a win exe under wine/ubuntu Karmic that needs to access and write to files owned by user 'www-admin'.  Group permissions are read only.  I have joined the grup 'www-admin', but I cannot find a way to change group permissions to rwx or to change owner to achieve this.  I have tried this as user 'www-admin', and I have edited /etc/sudoers with the line:
www-data ALL=(ALL) NOPASSWD:ALL so the password problem is solved.  Nothing helps.  Can someone give me a hint?

change file's owner to you and your group,
```
sudo chown <username>:<group> <file>
```

more info,
```
man chown
```

---

### Post by amalgamas on 2010-01-03
```
bf@bf-laptop:/media$ ls -l
totalt 48

drwsr-sr-x  4 www-data www-data     0 2009-09-30 17:55 Chaos

bf@bf-laptop:/media$ sudo chown <username>:<group> Chaos
chown: endring av eierskap på «Chaos»: Invalid argument
```sorry Norwegian, but something like "change of ownership on «Chaos»: Invalid argument"

The command is correct, and I have tried all combinations of chown and chmod that I can think of

---

### Post by konqueror7 on 2010-01-04
> **amalgamas said:**
> ```
bf@bf-laptop:/media$ ls -l
totalt 48

drwsr-sr-x  4 www-data www-data     0 2009-09-30 17:55 Chaos

bf@bf-laptop:/media$ sudo chown <username>:<group> Chaos
chown: endring av eierskap på «Chaos»: Invalid argument
```sorry Norwegian, but something like "change of ownership on «Chaos»: Invalid argument"

The command is correct, and I have tried all combinations of chown and chmod that I can think of

mmm...did you directly input it? it should be your username and group, try this instead...

```
sudo chown $USER:$USER **filenameHereOrDirectory**
```

this will change it to your username and group of a file...

also it maybe with the 'drwsr-sr-x', i forgot how to manipulate it, i'll try to look for it again,,,

---

### Post by konqueror7 on 2010-01-04
oh, and what folder/file are you really trying to gain permission?

also, regarding the 's's in the permission, is relevant for accessing system resources when using the file...

---

### Post by amalgamas on 2010-01-04
> **konqueror7 said:**
> oh, and what folder/file are you really trying to gain permission?

also, regarding the 's's in the permission, is relevant for accessing system resources when using the file...

I changed the fstab file from
```
//10.0.0.17/public/Chaos /media/Chaos cifs rw,iocharset=utf8,setuids,file_mode=0666,dir_mode=0777 0 0
```to
```
//10.0.0.17/public/Chaos /media/Chaos cifs rw,iocharset=utf8,uid=1000,gid=1000 0 0
```after sudo umount and sudo mount I got this:
```
drwsr-sr-x  4 bf       bf           0 2009-09-30 17:55 Chaos
```Now the files can be opened.  Generally file permissions are the only hurdle for me as a newbe ubuntu user.  Its like understanding ancient Greece and I do a lot of trying and (often) failing.  Apart from that my first 6 months with ubuntu have been great!

Next problem: the windows program I want to use did not install correctly under wine and crashes with 'invalid floating point operation'.  

Thank you for your help! The user forums are really helpful for us newbees!

---

### Post by konqueror7 on 2010-01-05
> **amalgamas said:**
> I changed the fstab file from
```
//10.0.0.17/public/Chaos /media/Chaos cifs rw,iocharset=utf8,setuids,file_mode=0666,dir_mode=0777 0 0
```to
```
//10.0.0.17/public/Chaos /media/Chaos cifs rw,iocharset=utf8,uid=1000,gid=1000 0 0
```after sudo umount and sudo mount I got this:
```
drwsr-sr-x  4 bf       bf           0 2009-09-30 17:55 Chaos
```Now the files can be opened.  Generally file permissions are the only hurdle for me as a newbe ubuntu user.  Its like understanding ancient Greece and I do a lot of trying and (often) failing.  Apart from that my first 6 months with ubuntu have been great!

Next problem: the windows program I want to use did not install correctly under wine and crashes with 'invalid floating point operation'.  

Thank you for your help! The user forums are really helpful for us newbees!

oh, the whole drive wasn't able to mount?! haha,,,with the wine problem you need to verify if it supports your app in [appdb.winehq.org]("appdb.winehq.org")

---

### Post by amalgamas on 2010-01-05
> **konqueror7 said:**
> oh, the whole drive wasn't able to mount?! haha,,,with the wine problem you need to verify if it supports your app in [appdb.winehq.org]("http://appdb.winehq.org")

...well, it mounted, but as you could see in my first message, with the wrong user (www-admin)

---

