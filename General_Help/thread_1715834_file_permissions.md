---
title: "file permissions"
date: 2011-03-27
forum: General Help
---

### Post by stigma-x11 on 2011-03-27
Setting up Apache2 and it stores the website in /var/www/ now my username has the root group set but its not letting me edit or add any files to the website folder. I am new to linux so I am sorry if this is a pointless question. Thanks for any help.

---

### Post by vivek.pandey on 2011-03-27
hi
have you tried changing permissions of the file
type this on terminal
chmod +x filename

---

### Post by koepked on 2011-03-27
if you:
# cd /var
# ls -al

and look at www, you'll probably see:
drwxr-xr-x

The r-x in the middle (if that's what yours is) is the group permissions for www, which don't allow writing (if a group member could write it would say rwx, like the first part, which is the permissons for the owner).

I wouldn't change any permissions (chmod), I would just use sudo to copy files to the directory:
# sudo cp filename /var/www/

---

