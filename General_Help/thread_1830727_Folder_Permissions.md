---
title: "Folder Permissions"
date: 2011-08-22
forum: General Help
---

### Post by Brooksy_FC on 2011-08-22
Hey All,

I'm trying to open some folders for my website. I have copied the new files over to file system/var/www, but all the files have a lock on them.

The only way I can edit them is with "sudo nautilus".

Is there anyway to allow me to edit these files without always entering this code?

---

### Post by ~!geek!~ on 2011-08-22
Visit : [http://www.linuxcommand.org/lts0070.php](http://www.linuxcommand.org/lts0070.php) to learn about permissions, in general.
 It will solve this problem you have as well as help you with Linux. Just go through it.

---

### Post by shubham1 on 2011-08-22
use 
sudo chmod 777 -R system/var/www/
and tell the result did it work in a terminal

---

### Post by Brooksy_FC on 2011-08-22
thanks for that link :)

I tried the command and it says: "chmod: cannot access 'system/var/www': No such file or directory"

---

### Post by shubham1 on 2011-08-22
you should type the actual location that you want go to home folder and go to location you want and then get the actual location i telled you as a example

---

### Post by zeroseven0183 on 2011-08-22
It seem like the directory system/var/www does not exist. Make sure you enter the correct path.

Check the owner and the permissions of the files under your directory by typing ```
ls -la
``` in the Terminal. That would give you a hint.

---

### Post by shubham1 on 2011-08-22
i think it should be /var/www/

---

### Post by nothingspecial on 2011-08-22
Rather than giving read write, execute, permissions to anyone which 777 would, I'd be inclined to continue using sudo (you should use gksudo for nautilus btw). That's the whole point.

---

### Post by Brooksy_FC on 2011-08-22
> **shubham1 said:**
> i think it should be /var/www/

YES!!! It's works!!! Thank you sooo much for your help guys. Can finally complete this website :D

---

### Post by shubham1 on 2011-08-22
> **Brooksy_FC said:**
> YES!!! It's works!!! Thank you sooo much for your help guys. Can finally complete this website :D
welcome

---

