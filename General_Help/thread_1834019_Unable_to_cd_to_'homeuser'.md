---
title: "Unable to cd to '/home/user'"
date: 2011-08-26
forum: General Help
---

### Post by mrosso10 on 2011-08-26
Hi, i've got this problem when i try to log in into my ubuntu. This was originated by a big mistake of mine (Sorry, i'm taking my first steps on linux). I executed this command into the directory '/home/user/Desktop':
sudo ln -s / .
And then the disaster began. I never could log in again with my user, only as root.
Any ideas about how to solve this problem?
Thanks!!

---

### Post by searchfgold6789 on 2011-08-26
Backup your data using a live cd if you can, man!!! I can't guarantee if this won't make things worse!!!
Okay, what I am assuming you did was type in the command:```
~/Desktop$ sudo ln -s /
```The only way to remove a symlink, which is what you created, is either unlink (which is discouraged) or rm. 
The first method:
```
unlink /home/user/Desktop
```
If that doesn't work, what you should do is simply remove (as root) and re-create (as user) your desktop.
```
sudo rm -rv /home/user/Desktop
mkdir /home/user/Desktop
```

---

