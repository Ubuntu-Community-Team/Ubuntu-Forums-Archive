---
title: "Cannot empty trash"
date: 2006-04-10
forum: General Help
---

### Post by leftyman on 2006-04-10
Hello:


Some files in my trash cannot be deleted cause I dont have the correct right over them

how do I solve thisP?

thanks

---

### Post by philipacamaniac on 2006-04-10
What happened is you sent files to the trash that were owned by root (most likely). This happens a lot when you do a "sudo make install" and then trash the make directory.

Anywho...

In a terminal:
```

cd ~/.Trash

``` and then
```

sudo rm -r $FILENAME

``` and replace $FILENAME with the name of the folder or file that refuses to be emptied from the trash.

---

### Post by andreasmascher on 2007-12-08
Thanks for the reply. I figured that it would be a little bit more convenient to simply empty the trash after doing 

```

sudo nautilus /home/name/.Trash

```

because of a large amount of different files. Or can I remove all the contents of a folder in a terminal?

---

### Post by CatKiller on 2007-12-08
**man rm** has all of the information on how to use rm to delete files from the Terminal. ```
sudo rm -r ~/.Trash/*
``` should remove everything in your ~/.Trash folder. If you have access to other partitions, they will also have a .Trash-<username> folder that might have some stuff in too.

---

### Post by andreasmascher on 2007-12-08
wonderful, thx!  :-\"

---

### Post by lakotajames on 2008-05-29
I am having the same problem, but "cd ~/.Trash" gives me this: ```
lakota@Ubuntu:~$ cd ~/.Trash
bash: cd: /home/lakota/.Trash: No such file or directory

```
none of the other commands work either, for the same reason.

---

### Post by powerpleb on 2008-05-29
> **lakotajames said:**
> I am having the same problem, but "cd ~/.Trash" gives me this: ```
lakota@Ubuntu:~$ cd ~/.Trash
bash: cd: /home/lakota/.Trash: No such file or directory

```
none of the other commands work either, for the same reason.

Try 
```
sudo chown -R yourusername /home/yourusername 
```
to make everything in your home dir yours

then click on trashcan and Empty Garbage Bin as usual

---

### Post by Bubba64 on 2008-05-29
All the terminal stuff is cool but I believe if you highlight (right click) on any file hold down shift and hit delete on the keyboard you can delete anything. If it is not even in trash this method also deletes without being put in trash

---

### Post by A*p on 2008-07-17
I had this problem and non of the suggestions worked. *(I did not try the chown suggestion by powerpleb though)*  I emptied the files in the following way though.

I found that my trash was located here:

> /home/**your_user_name**/.local/share/Trash/files

So I just went their and deleted the files from the command line with root privileges.

Their is also an info directory in the Trash folder that should have a text file relating to your selected deleted items these too can be deleted.

---

### Post by lukjad on 2008-07-17
Here's what worked for me:
sudo rm -r ~/.local/share/Trash/files/

---

### Post by Jompa on 2008-07-17
Had the same problem, but this one solved it, thanks Bubba64 :D
> **Bubba64 said:**
> All the terminal stuff is cool but I believe if you highlight (right click) on any file hold down shift and hit delete on the keyboard you can delete anything. If it is not even in trash this method also deletes without being put in trash

---

### Post by soxs on 2008-07-17
> **powerpleb said:**
> Try 
```
sudo chown -R yourusername /home/yourusername 
```
to make everything in your home dir yours

then click on trashcan and Empty Garbage Bin as usual
It's not about the ownership, its about mod. So you should adjust edit rights via
```
sudo chmod 755 -Rvf ~/.local/share/Trash
```

---

