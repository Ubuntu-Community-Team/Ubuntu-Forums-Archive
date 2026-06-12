---
title: "php stopped working! :S"
date: 2006-04-27
forum: General Help
---

### Post by frup on 2006-04-27
i just went to make a php file in var/www and i get this message

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/phpinfo.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

i tried putting plain HTML in it and just putting phpinfo() but it didn't change ... ok thats cool maybe i need to reinstall PHP but THEN WHY ARE ALL MY OTHER SCRIPTS WORKING!!! :S this is so wierd lol :(

any ideas?

PS
when i edited an old file and saved it this worked too but if i get this file and click save as it doesnt work.

---

### Post by frup on 2006-04-27
ok i seem to have fixed this before anyone replied... finding out why this happens would be nice... is this a bug?

basically if i make file by right clicking and and creating empty file and renaming it x.php and saving it etc... i get the message (included if i include this in a working.php file) 
IF i create the file from blank and save as in Gedit it works :S why does creating a file in gui not work?

i noticed that as i went to save one the option if came up with was file.php~ not php (in the history type guess thing)
does creating a blank file in gui automatically create ~ at the end of the file?

---

### Post by cskeide on 2006-04-27
This sounds like a problem with file permissions. Try creating two files, one with each of the methods you described. Then open a terminal and type:
```
cd /var/www
ls -al
```
Check if file permissions are different for the files you created.

---

### Post by frup on 2006-04-27
yeah i think you're right

the files that didnt work we

RW-------
the files that did were

RW-R--R--

obviously php wasnt allowed to read them :D lol

so how do i make it so (maybe only in /www) any file created will by default be rwrr?

---

