---
title: "Don't have permissions to save to a folder"
date: 2010-01-20
forum: General Help
---

### Post by bobbins on 2010-01-20
Okay, so running latest ubuntu 9.10 karmic koala. I installed from the terminal PHP and can browse to the localhost and everything looks cool.

I try to use gedit or quanta to save a file to /var/www/

Which is where the test index.php is located but I don't have the correct permissions! I am logged in as the same user I installed ubunutu under which should give me all the rights I need.

I am guessing I need to give myself permission to write into this folder? Any help would be appreciated.

---

### Post by nothingspecial on 2010-01-20
```
gksudo nautilus
``` will open up your file browser with root permissions.

---

### Post by bobbins on 2010-01-20
I tried that and it works as you suggest but even giving myself all permissions for the folder and contents i.e read/write files etc still says I do not have permission to save a file into that folder. :(

---

### Post by n0dix on 2010-01-20
Do:
```
sudo gedit
```
Then open the index file, change something and save it. 
You should change the file.
Do:
```
ls -la /var
```
```
ls -la /var/www/
```

---

### Post by nothingspecial on 2010-01-20
You don`t change the permissions of folders outside of your home directory. You give yourself the permission to do it.
If you want to edit or create a file in there

```
gksudo gedit /var/www/file
```

---

### Post by bobbins on 2010-01-20
Thanks for the info. It worked! I was really having a hard time so thank you very much for helping me out. 

Made my day :)

---

### Post by n0dix on 2010-01-20
> **bobbins said:**
> Thanks for the info. It worked! I was really having a hard time so thank you very much for helping me out. 

Made my day :)

Don't forget to add the SOLVED tag to the title.

---

