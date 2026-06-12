---
title: "Permission for var/www"
date: 2010-12-26
forum: General Help
---

### Post by Ron Roy on 2010-12-26
Hi, Using apache server. Everything is working but i cannot delete files in this folder. It has to do with permissions but I am not sure how to change this.
Need some help.

---

### Post by karthick87 on 2010-12-26
```
sudo rm -R /var/www
```

---

### Post by Ron Roy on 2010-12-26
Thanks for the reply, however the next thought is does this allow me to access the file system and simply delete the file or is this done with commands. I am new to ubuntu and not familiar with all this terminal stuff

---

### Post by Ron Roy on 2010-12-26
Not sure if you received reply

---

### Post by karthick87 on 2010-12-26
If you are confused,then in terminal type
```
gksudo nautilus
```
It will open a nautilus browser with root previlges.Navigate to /var/www and then delete the files..

---

### Post by Ron Roy on 2010-12-26
Just lost my directory. what do i do now?

---

### Post by karthick87 on 2010-12-26
```
sudo mkdir /var/www
```

---

### Post by Ron Roy on 2010-12-26
Great stuff. The var/web/web1 folders are gone.

---

### Post by cgroza on 2010-12-26
> **Ron Roy said:**
> Great stuff. The var/web/web1 folders are gone.
Of course they are, you just deleted them.
Before, you could do sudo chmod 777 /var/www and it should be able to do anything.

---

### Post by lisati on 2010-12-26
> **karthick87 said:**
> ```
sudo rm -R /var/www
```

[SIZE="5"]Caution:[/SIZE] [SIZE="2"]This is likely to delete more than you might want.[/SIZE]


If you've accidentally run this, and used the "... mkdir ..." command to get /var/www back, chances are you'll have to restore the files you want from a backup.

---

### Post by WorMzy on 2010-12-26
> **karthick87 said:**
> ```
sudo rm -R /var/www
```

Whoa, whoa, whoa! There was no call for that command; OP didn't say they wanted to remove everything in that folder. You might want to edit your post so that it's clearer what that command will do.

Ron, if you used that command, then everything you had in /var/www is gone. If you had anything you wanted to keep in there, then you may be able to recover it with data recovery software, such as testdisk. If, as I think Karthick assumed, you've only just installed apache, then you can just recreate the folder:
```
sudo mkdir /var/www
```

You can use the command "chown" (or "chgrp") to gain ownership (or group ownership) of the folder:
```
sudo chown **_USERNAME_** /var/www
```
```
sudo chgrp **_GROUP_** /var/www
```
(replace **_USERNAME_**/**_GROUP_** with your username or group)

or, as karthick suggested, use nautilus under root (gksudo nautilus) to browse/delete files. Changing ownership is generally fine so long as the apache user can read and execute the contents of the folder.

---

### Post by cgroza on 2010-12-26
Always think a little before you run commands like that. Sometimes people make mistakes and you have to make sure that you don't get an unpleasant surprize like this one.

---

### Post by Ron Roy on 2010-12-26
I have since re-installed 9.10 and apache. This sure seems tough compared to windows, but lets try again. I have placed three web sites in /var/www/web/ and I figured out how to use my editor and gimp to save to these files. It's not so critical, but i would like to remove a document and don't know how. Using wamp in windows was a breeze, this seems too much like work. How do gain access to removing something without total disaster? Not too up on commands. Thanks for any help.

---

### Post by WorMzy on 2010-12-26
Well, the first point would be to use the commands I listed.

At the moment, root (the highest level user) owns all the files. This is hard to understand if you're coming from Windows, but try to imagine that "root" is an admin, while your user is a restricted user.

Typically, on Linux, there is only one admin, and this is "root", everyone else is a "restricted user". However, certain restricted users are able to use "sudo", which makes "root" perform tasks in lieu of the user. Read this webpage for more details: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

My chown/chgrp commands will give *your* user the rights to delete individual files and folders. But, if you choose not to use them, using "sudo" will allow your user to remove files without them. e.g.
```
sudo rm /var/www/web/page.html
```
will remove the page.html file from /var/www.

---

