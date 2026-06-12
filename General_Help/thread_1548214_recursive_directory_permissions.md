---
title: "recursive directory permissions"
date: 2010-08-08
forum: General Help
---

### Post by bcdudley on 2010-08-08
I have a process running on one of my machines that will drop a file into a directory for a user to pick up via samba. I have set the permissions to what I thought would be correct, but it is not working. I need for users in the dbusers group to be able to retrieve files out of this folder and delete the file from the directory. Currently, they are able to access the file, but they cannot delete it. I have also set the umask to 000, but that did not help any.

I run the command sudo chmod -R 777 /dbfiles/
and I get:
drwxrwxrwx   4 root dbusers  4096 2010-07-21 02:20 dbfiles

How do I get the permissions to be inherited by newly created files or files that have been moved into this directory.

Thank you.

---

