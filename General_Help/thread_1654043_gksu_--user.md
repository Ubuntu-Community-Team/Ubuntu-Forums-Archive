---
title: "gksu --user"
date: 2010-12-27
forum: General Help
---

### Post by spezticle on 2010-12-27
i need some help getting gksu to run programs.

the goal is to be logged in as user1 and run firefox or google-chrome with user2 's settings stored in their own home directory.

i'm trying the following with no success:
```
user1@hostname:~$ su user2
Password: 

user2@hostname:/home/user1$ google-chrome 
No protocol specified

(google-chrome:17144): Gtk-WARNING **: cannot open display: :2.0
```
```
user2@hostname:/home/user1$ firefox
No protocol specified
No protocol specified
Error: cannot open display: :2.0
```
```
user2@hostname:/home/user1$ gedit
No protocol specified

(gedit:17162): Gtk-WARNING **: cannot open display: :2.0
```

---

### Post by sisco311 on 2010-12-27
You have to add user2 to the list of users allowed to make connections to the X server:
```
xhost SI:localuser:**user2**
su - **user2**
firefox
exit
xhost -SI:localuser:**user2**
```
or
```
xhost SI:localuser:**user2**
sudo -u **user2** -i
firefox
exit
xhost -SI:localuser:**user2**
```
or
```

xhost SI:localuser:**user2**
gksu --user **user2** firefox
xhost -SI:localuser:**user2**

```
EDIT: and you have to start a login shell (su **-** or sudo **-i**), in order to make sure that the HOME environment variable is reseted.

[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

