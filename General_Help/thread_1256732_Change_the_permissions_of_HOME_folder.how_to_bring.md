---
title: "Change the permissions of HOME folder.how to bring it back to the default permission"
date: 2009-09-03
forum: General Help
---

### Post by Angeline Aarthi on 2009-09-03
Hello,  I changed the folder permission of my Home directory by mistake and it is throwing up the following message while system start up.

User's $HOME/.dmrc is being ignored. THis prevents the default sesssion and language fron being saved File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

The changes I did were,
  
   sudo chown 777 weblab
  And also changed the permissions by right clicking the home folder,weblab, and changing the permissions for ser,group and others to read and write.

Can some one help me in resolving this? Due to this I'm not able to access by phpmyadmin folder. It says Wrong permissions on configuration file, should not be world writable!

---

### Post by egalvan on 2009-09-03
[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

---

