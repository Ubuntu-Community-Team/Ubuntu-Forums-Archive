---
title: "Can't change permissions"
date: 2011-08-24
forum: General Help
---

### Post by Shawn503 on 2011-08-24
Whenever I try to change the permissions on anything it says that I don't have permission to change the permissions. 

For example, when I input:  

chmod a+wrx /Home/Shawn/folder

It says:  

chmod: changing permissions of '/Home/Shawn/folder': Operation is not permitted

Also sometimes when I try to move a file, it says it is not permitted, even if the permissions of the file are set to rwx for all users

---

### Post by mike555 on 2011-08-24
use sudo , or gksudo natilus in terminal (when you type your password it won't show)

---

### Post by thefasterblueone on 2011-08-24
/Home/Shawn/folder should be /home/Shawn/folder. home is lower case.

---

### Post by searchfgold6789 on 2011-08-24
Bad: :(
```
chmod a+wrx /Home/Shawn/folder
```
Good: :)
```
gksu chmod a+wrx /Home/Shawn/folder
```

---

### Post by MG&amp;TL on 2011-08-24
Just to clarify, 

```
sudo <chmod whatever>
```

is what you put in, then it will ask for administrator password, then you're away.

EDIT: Damn, beaten to it. :D

---

