---
title: "Permissions on folders"
date: 2011-01-03
forum: General Help
---

### Post by mraccine on 2011-01-03
I'm a Ubuntu newbie. We have a development server not acessible to the public used for testing which was setup for us.
 
When attempting to have my PHP scripts upload an image to a folder, I have to CHMOD the folder to 777. Ideally, when a folder is created it has permissions set to 755 - I want to be able to upload to them.
 
Is there a way to change permissions to allow the PHP scripts that run to be able to write to a folder? I know it has something to do with owner or group, but I don't know where to start. 
 
Any help is appreciated.

---

### Post by lithopsian on 2011-01-03
Who do the PHP scripts run as?  You can change the owner of the directory (chown) to the same user and PHP will then get the "7" bit instead of the "5" bit :)  There are other solutions if you don't want that user to own the directory.

---

### Post by mraccine on 2011-01-03
I'm not sure which is owner or group, bit when I look at the files it reads
drwxr -xr-x  office  coworker
 
I assume "office" is owner and group is "coworker".
 
I pretty much do the only PHP writing in our small 2 person office, so anyone here should be able to write to the folders.

---

