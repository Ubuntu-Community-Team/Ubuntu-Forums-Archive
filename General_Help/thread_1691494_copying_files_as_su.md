---
title: "copying files as su"
date: 2011-02-20
forum: General Help
---

### Post by dwlamb on 2011-02-20
Good day,

I'm somewhat new to Linux/Ubuntu so pardon me if this is posted elsewhere.  A google search didn't answer my topic.

Is there a method at the command line to copy files from one location to another and retain the source files group and user?

I'm migrating some MySQL files from one machine to another.  I want to back-up the original files in the directory presently.  They have owner:group of mysql, some have owner:group root:mysql and so on.  To copy them under cli or Nautilus everything changes to root for I execute sudo cp....  or gksudo nautilus and copy via gui.

Since it is MySQL data I could simply do a dump of the database and restore it on the other machine.  But there's about 20 db's and I want to do this via a copy for it will be faster - at least that is what I think. :-)

Thanks for taking the time to read this

---

### Post by Old *ix Geek on 2011-02-20
Use the 'preserve' and 'recursive' arguments with the 'cp' (copy) command:
```
cp -pR old_location new_location
```

This will copy everything under **old_location** to **new_location** and retain ownership, permissions, timestamps, etc.

Add the 'verbose' flag if you want to see the files as they're being copied:
```
cp -pRv old_location new_location
```

---

### Post by dwlamb on 2011-02-20
Thanks a lot!  Exactly what I was looking for.

> **Old *ix Geek said:**
> Use the 'preserve' and 'recursive' arguments with the 'cp' (copy) command:
```
cp -pR old_location new_location
```

This will copy everything under **old_location** to **new_location** and retain ownership, permissions, timestamps, etc.

Add the 'verbose' flag if you want to see the files as they're being copied:
```
cp -pRv old_location new_location
```

---

### Post by Mozesibe on 2011-02-20
Hay Dwlamb seems you know a lot already i just joined, i usually develop and deploy my web apps on windows-i joined Ubuntu and have Installed Apache,Php and Mysql..but i find it hard moving my project fills to the /var/www-dialogs alway say 'i dont have d permission'

i moved some tru terminal yet it dosent show went i want to access dem from d web brower \

plz guys put me tru if u can!

---

### Post by Old *ix Geek on 2011-02-20
> **dwlamb said:**
> Thanks a lot!  Exactly what I was looking for.You're welcome. Glad it worked as wanted! :)

---

### Post by dwlamb on 2011-02-20
First off, if you're going to seek help on forums such as these, put a little more effort in what you write. I had to read this a few times just to make sense of what you were saying.  Now, to solve your challenge.

A key to Linux and all distributions of it (e.g., Ubuntu, Debian, openSUSE, etc.) is **root**.  'root' has control of the whole system.  You have control (i.e., read/write, delete) of files under your home directory.  You are the owner of those files. 

In the /var/www directory, where you want to store your web site files that is owned by **root**.  That is why you can't copy the files to that directory.

The way around this is to become root temporarily.  To copy your files, from your home directory to www open a command shell and type the following.

```
sudo cp -r /home/mozesibe/Documents/webs/ /var/www/ 
```

The source of the files "/home/mozesibe/Documents/webs/" can change.  I just chose that for the purposes here.  The destination "/var/www/" has to be that, if you are copying web site source code files.

Be very careful when you become the super-user using the 'sudo' command.  You're essentially telling Linux "Hands-off. I'm taking control of the whole computer."  You have just crossed over to have the potential to mess up your system if you don't know exactly what you're doing and know 100% what impact it will have.


> **Mozesibe said:**
> Hay Dwlamb seems you know a lot already i just joined, i usually develop and deploy my web apps on windows-i joined Ubuntu and have Installed Apache,Php and Mysql..but i find it hard moving my project fills to the /var/www-dialogs alway say 'i dont have d permission'

i moved some tru terminal yet it dosent show went i want to access dem from d web brower \

plz guys put me tru if u can!

---

