---
title: "PHP and  permissions"
date: 2010-12-19
forum: General Help
---

### Post by creata.physics on 2010-12-19
Hello, I'm somewhat new to linux and recently decided to use the OS again to help me with developing.  I have gotten my home server set up and running just fine, changing file permissions to make them writeable was okay, I changed that just fine.  I have a PHP script that generates a cache, I use a function called fwrite to generate the file, the problem is this...

I have a cache directory with 777 permissions, I can write files to the directory but after I do they have a lock next to the file icon, when viewing the permissions it shows that the file was created by 'nobody'.  When I go into my terminal and change my chmod settings to 777 the lock icon disappears and then I can use the file, but once another cache file is replaced that specific file is locked, so basically after my script that automatically generates files at specific times and intervals all get locked and the cache folder permissions seem to change, since by changing the folder perms in my terminal it removes the lock.

Is there any fix with this? has this ever happened before?

Also this seemed best fitting to place this topic, I did some searching and did not find anything related to this on google or here.  Thanks in advance.

---

