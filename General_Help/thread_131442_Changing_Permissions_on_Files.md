---
title: "Changing Permissions on Files"
date: 2006-02-16
forum: General Help
---

### Post by TomAnthony on 2006-02-16
I recently moved all my music and other files from my ntfs partition to my linux one, and all the permissions are read only. Is there a way to change all the permissions to read/write/modify without having to do it one file at a time?

---

### Post by coolclassic on 2006-02-16
By using konqueror you can change permissions all a one time:
In a terminal

kdesu konqueror

This gives you root privileges and you can change the permissions of the folder your files are in and tick apply to all. you can also do this from the command line by using chmod.

---

### Post by TomAnthony on 2006-02-16
[QUOTE=coolclassic]By using konqueror you can change permissions all a one time:
you can also do this from the command line by using chmod.[/QUOTE]

What would be the command line to use with chmod?

---

### Post by alfonz on 2006-02-16
i don't know how to chmod a directory but in terminal

sudo chmod 755 /path/to/file/name will do the trick for a file

---

### Post by TomAnthony on 2006-02-16
I keep getting an unspecified error when using Konqueror.

---

### Post by aysiu on 2006-02-16
Let's say you moved them all to a folder called /home/tomanthony/music
Open up a terminal and type ```
sudo chown -R tomanthony:tomanthony /home/tomanthony/music
``` to **ch**ange the **own**ership to you (from root).

If you want, you can also make it still belong to root but be accessible to everyone: ```
sudo chmod -R 777 /home/tomanthony/music
```

---

### Post by alfonz on 2006-02-16
Thanks aysiu, I learn something new everyday.

---

### Post by TomAnthony on 2006-02-16
I tried that but it didn't work (no error). They are all in their own subfolders. Does that make a difference?

---

### Post by TomAnthony on 2006-02-16
Actually, I tried the sudo chmod -R 777 /home/tomanthony/music command, and it worked. Thank you ever so much. This has been so helpfull. And it was very quick!

---

### Post by aysiu on 2006-02-16
[QUOTE=TomAnthony]I tried that but it didn't work (no error). They are all in their own subfolders. Does that make a difference?[/QUOTE] It shouldn't. That's what the **-R** means--recursively, so that the changes apply to all the subfolders as well.

You tried both *sudo chmod* **and** *sudo chown*? Neither worked?

---

### Post by wrtrdood on 2006-02-16
BTW, 777 is bad security.  The default should be:

644 for files which equates to -rw-r--r--
755 for directories which equates to drwxr-xr-x

---

### Post by aysiu on 2006-02-16
[QUOTE=wrtrdood]BTW, 777 is bad security.  The default should be:

644 for files which equates to -rw-r--r--
755 for directories which equates to drwxr-xr-x[/QUOTE] That's why I said: [quote=me earlier]**If you want,** you can also make it still belong to root but be **accessible to everyone:**[/quote]

---

