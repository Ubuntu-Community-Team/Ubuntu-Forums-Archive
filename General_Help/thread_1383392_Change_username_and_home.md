---
title: "Change username and home"
date: 2010-01-17
forum: General Help
---

### Post by aum11 on 2010-01-17
I am passing my laptop to a friend.  The laptop is running Karmic.

I need to change the name of Home from my name to my friends.  That is, change the username and password, but also the name of Home from my name to friend's name.

How can I do this please?

Thanks.

---

### Post by SuperSonic4 on 2010-01-17
One line at a time

```
sudo -i
useradd -m -G audio,floppy,lp,optical,admin,storage,video,wheel,power,scanner -s /bin/bash *username*
passwd *username*
**cp -Rv /home/[COLOR="Blue"]your_user[/COLOR]/* /home/*username*/**
[COLOR="Red"]chown -R *username*:*username* /home/*username/*[/COLOR]
userdel -r [COLOR="Blue"]your_user[/COLOR]
```

Omit the line in bold if you don't want the new user to have your files and folders

The line in red may not be necessary, depending on how cp works.

*username* is your friend's username
[COLOR="Blue"]your_user[/COLOR] is your current username

---

### Post by sisco311 on 2010-01-17
add a new initial login group for the new user:
```
sudo addgroup **newuser**
```

change the name of the home directory, the login name and initial login group:
```
sudo usermod -m -d /home/**newuser** -l **newuser** -g **newuser** **olduser**
```
-m = move the home directory content to the new location.

set the correct group:
```
sudo chgrp -R **newuser** /home/**newuser**
```

NOTE: You may have to change manually the paths in some application. i.e. the download directory in firefox.

---

