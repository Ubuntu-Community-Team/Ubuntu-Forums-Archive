---
title: "Samba permissions when creating a new folder through Windows"
date: 2010-04-01
forum: General Help
---

### Post by jackaninny on 2010-04-01
I've got a small issue that when a Windows user creates a new folder through Windows Explorer (from the menu or by right clicking) the new folder is only accessible to that particular user. 

Example:

user SABKAR (member of the HR group) creates a new folder called MarcTestMenu in a shared Samba directory through Windows Explorer:

ls -l
drwxr-sr-x  2 sabkar hr       48 2010-04-01 10:36 MarcTestMenu

At this point user MORAMY cannot copy a file or open the directory MarcTestMenu. MORAMY gets a 'not accessible' error message in Windows.

If I su to the Samba box and issue this command:

root@logan:/home/hr# chmod 6770 MarcTestMenu/

I now get the follow permissions on the directory:

drwsrws---  2 sabkar hr       48 2010-04-01 10:38 MarcTestMenu

and user MORAMY can access and copy files to the directory.



Any thoughts on how I can get the correct default permissions when users create directories through Windows?

Thanks in advance.

---

### Post by blueridgedog on 2010-04-01
You need to set the default mask for directory creation in samba.

see:

[http://lists.samba.org/archive/samba/2003-March/063429.html](http://lists.samba.org/archive/samba/2003-March/063429.html)

and 

[http://ubuntuforums.org/showthread.php?t=815551](http://ubuntuforums.org/showthread.php?t=815551)

---

