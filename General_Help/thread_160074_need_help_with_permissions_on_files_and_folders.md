---
title: "need help with permissions on files and folders"
date: 2006-04-14
forum: General Help
---

### Post by x3non on 2006-04-14
Hi all :D

i have a folder with alot of files and subfolders into it.

Now, for secuirity reasons i need to modify the permissions:

755 for the folders and 644 for the files.

Since are really a lot of files and subforders, i cannot do this by hand (unless i have 10 hours to trash away ;) ).

Does anyone has a script to automatically change permissions?


tnx,

xenon

---

### Post by Derek Djons on 2006-04-14
If I'm correct you can use the terminal to change the permissions of one folder. If you add the right options it will change the permission of all folders / files in that folder.

1. Browse using CLI to your folder you want to change permissions.
2. Use 'chmod -r <foldername> 664
3. Use 'man chmod' or 'chmod man' to read the manual about chmod options.

---

### Post by x3non on 2006-04-14
of course Derek, but using the "-R" option, it will change to 644 the subdirs too!

example:
```

drwxr-xr-x   6 www-data www-data 4,0K 2005-09-28 22:04 admin
-rw-r--r--   1 www-data www-data  21K 2005-09-28 22:04 admin.php
-rw-r--r--   1 www-data www-data 2,4K 2005-09-28 22:04 backend.php
drwxr-xr-x   2 www-data www-data 4,0K 2005-10-29 18:40 blocks
drwxr-xr-x  12 www-data www-data 4,0K 2006-04-08 22:16 cacti
-rw-r--r--   1 www-data www-data 5,5K 2006-03-15 18:31 config.php
drwxr-xr-x   2 www-data www-data 4,0K 2005-11-21 18:18 db
-rw-r--r--   1 www-data www-data 4,2K 2006-04-13 13:15 favicon.ico
-rw-r--r--   1 www-data www-data 3,0K 2005-09-28 22:04 footer.php
-rw-r--r--   1 www-data www-data 1,9K 2005-09-29 12:31 header.php
drwxr-xr-x  11 www-data www-data 4,0K 2005-09-28 22:05 images

```

i need to set for all files 644, and for dirs 755.

Then, in the subdir "admin" i need to have the same situation:

```

-rw-r--r--  1 www-data www-data    12 2005-09-28 22:04 admin.php
drwxr-xr-x  2 www-data www-data 4,0K 2005-09-28 22:05 case
-rwxr--r--  1 www-data www-data    0 2005-09-28 22:04 index.html
drwxr-xr-x  2 www-data www-data 4,0K 2005-09-28 22:05 language
drwxr-xr-x 2 www-data www-data 4,0K 2005-09-28 22:05 links
drwxr-xr-x  2 www-data www-data 4,0K 2005-10-30 20:55 modules

```


i hope to be more clear now ;)

bye!!

---

### Post by Derek Djons on 2006-04-14
[QUOTE=x3non]of course Derek, but using the "-R" option, it will change to 644 the subdirs too!

example:
```

drwxr-xr-x   6 www-data www-data 4,0K 2005-09-28 22:04 admin
-rw-r--r--   1 www-data www-data  21K 2005-09-28 22:04 admin.php
-rw-r--r--   1 www-data www-data 2,4K 2005-09-28 22:04 backend.php
drwxr-xr-x   2 www-data www-data 4,0K 2005-10-29 18:40 blocks
drwxr-xr-x  12 www-data www-data 4,0K 2006-04-08 22:16 cacti
-rw-r--r--   1 www-data www-data 5,5K 2006-03-15 18:31 config.php
drwxr-xr-x   2 www-data www-data 4,0K 2005-11-21 18:18 db
-rw-r--r--   1 www-data www-data 4,2K 2006-04-13 13:15 favicon.ico
-rw-r--r--   1 www-data www-data 3,0K 2005-09-28 22:04 footer.php
-rw-r--r--   1 www-data www-data 1,9K 2005-09-29 12:31 header.php
drwxr-xr-x  11 www-data www-data 4,0K 2005-09-28 22:05 images

```

i need to set for all files 644, and for dirs 755.

Then, in the subdir "admin" i need to have the same situation:

```

-rw-r--r--  1 www-data www-data    12 2005-09-28 22:04 admin.php
drwxr-xr-x  2 www-data www-data 4,0K 2005-09-28 22:05 case
-rwxr--r--  1 www-data www-data    0 2005-09-28 22:04 index.html
drwxr-xr-x  2 www-data www-data 4,0K 2005-09-28 22:05 language
drwxr-xr-x 2 www-data www-data 4,0K 2005-09-28 22:05 links
drwxr-xr-x  2 www-data www-data 4,0K 2005-10-30 20:55 modules

```


i hope to be more clear now ;)

bye!![/QUOTE]

Sorry, my fault. I wasn't reading right :)

---

### Post by albinoloverats on 2006-04-14
Try ```
chmod -R 755 *
find -type f -print0|xargs -0 chmod 644
```

---

### Post by albinoloverats on 2006-04-14
*EDIT: double post - a little to "click happy" on the quick post button :oops:

---

### Post by x3non on 2006-04-14
[QUOTE=albinoloverats]Try ```
chmod -R 755 *
find -type f -print0|xargs -0 chmod 644
```[/QUOTE]



it worked perfectly!!!

thanks a lot! 

;)

Xenon

---

### Post by robenroute on 2006-04-14
albinoloverats,

This solution of yours is great for all sorts of things. I wasn't aware of the xargs command. Perhaps I should be reading up on the basic Linux commands, instead of reading another John Irving....:rolleyes:

---

### Post by immeëmosol on 2007-07-24
```
#There's also this nice option for chmod that is a big X.
   #to do something like this:
      #for directories:
         chmod -R 755 ./directory

      #for files:
         chmod -R 644 ./directory

   #you could for instance do:
      chmod -R u=rwX,g=rX,o=rX ./directory

   #it would give
   #    user     read, write and execute rights on the directory//folder specified
   #    group   read and execute rights on the directory//folder specified
   #    others  read and execute rights on the directory//folder specified

#But I kind of really like this xargs as well...   :)
```

---

