---
title: "No root access"
date: 2010-06-28
forum: General Help
---

### Post by =ChAoS= on 2010-06-28
Hi, i'm currrently renting a dedicated server running Ubuntu 8.04 desktop and have seen a couple of problems with permissions.
 
It appears that i'm only an Admin and there fore cant edit/install certain things. 
 
Is it normal to not get root access in these circumstances? I have sent in a support ticket but don't know how long the reply will take.
 
Also i can only ftp to it as annonymous which i doubt is very secure and don't see any directories but then it might just be that i need to configure users or something on ubuntu and not just log in as Admin or create a file path of some description.
 
Thanks for any advice ... =ChAoS=

---

### Post by endotherm on 2010-06-28
what specifically are you running/doing?

ubuntu uses the sudo system to approve administrative actions, so whenever you are about to do somthing administery, add 'sudo ' to the beginning of your command. if the command runs a gui app, then use 'gksu' to do the same thing. do you think this is the issue?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by =ChAoS= on 2010-06-28
Thanks for the link i'm reading up now. 
 
The file i tried to edit was vsftpd with gedit so maybe i wasn't supposed to edit it tho the tutorial i follwed said i could and should change a couple of things. 
 
I'm very new at linux. :lolflag:

---

### Post by endotherm on 2010-06-28
once you get used to it, you will probably really like sudo. it's a far more elegant than UAC, and a good bit more effective as well. like UAC, it allows you to run as a limited user, but to take admin privileges on demand.

---

