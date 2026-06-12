---
title: "Vsftpd"
date: 2011-03-25
forum: General Help
---

### Post by czerdrill on 2011-03-25
I'm running an ubuntu server, and I have vsftpd installed.  However, I don't think it's being "used" when I try to connect to ftp.

The reason I'm wondering is if I check the vusers file it is empty.  However, I had set up an ftp user by using the command useradd -g ftp-users -d /path/to/their/directory username and I am able to connect to ftp through that user.  So, I'm not sure how or why that works.

How would I add a vsftpd user?  My main thing is restricting the created user to their directory and subdirectories only.  Don't want them to be able to browse above their directory.  The "useradd" user is able to browse all directories which I don't want. 

Is there some separate command to add vsftpd users?  In vsftpd.conf chroot_local_user is set to YES and uncommented...so how do I actually make this work??

---

### Post by czerdrill on 2011-03-27
bumppp

---

### Post by czerdrill on 2011-03-30
anyone?  seriously...im sure its a misconfiguration on my part, but i cant figure it out...

---

### Post by Sidewinder1 on 2011-04-02
czerdrill, I apologize, I definitely can not answer your question. :(
However, I found the link below very helpful. If you have already perused it, I apologize for "getting your hopes up".
In either event, good luck!

Side



[http://ubuntuforums.org/showthread.php?t=518293&highlight=vsftpd](http://ubuntuforums.org/showthread.php?t=518293&highlight=vsftpd)

---

