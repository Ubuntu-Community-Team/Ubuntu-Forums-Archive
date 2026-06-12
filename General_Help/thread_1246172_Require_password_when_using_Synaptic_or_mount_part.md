---
title: "Require password when using Synaptic or mount partitions"
date: 2009-08-21
forum: General Help
---

### Post by Operan on 2009-08-21
Formerly, whenever using Synaptic or mount partitions, my Ubuntu requires to enter password. Yesterday I tick the option : Remember the password so it doesn't require password anymore. How do I make Ubuntu ask password when necessary again?

---

### Post by Soapy.Illusions on 2009-08-21
I am pretty sure in your Applications you have a program call Key Ring, or something like that
 
All saved information and settings should be available there

---

### Post by Operan on 2009-08-22
I run "Passwords and Encryption Keys", select tab "Passwords". I found 2 items: Password: default and Password: login. I deleted both of them but my system still  doesn't require passwords. Any help esle?

---

### Post by XxionxX on 2009-08-22
My package manager doesn't have a remember the password option/checkbox did you install a password manager of some sort? I think that you are supposed to be asked for the root password every time. I know that I wouldn't let my computer be vulnerable like that. There is a reason you are asked every time, because you are granting root privileges.

Edit:
This thread might help [http://brainstorm.ubuntu.com/idea/15272/](http://brainstorm.ubuntu.com/idea/15272/). It also says that this is not a feature so... I don't really know how you rid yourself of the root password prompt unless you did some hack that you didn't post?? I hope that helps.

---

### Post by Operan on 2009-08-22
> **XxionxX said:**
> My package manager doesn't have a remember the password option/checkbox did you install a password manager of some sort? I think that you are supposed to be asked for the root password every time. I know that I wouldn't let my computer be vulnerable like that. There is a reason you are asked every time, because you are granting root privileges.

Edit:
This thread might help [http://brainstorm.ubuntu.com/idea/15272/](http://brainstorm.ubuntu.com/idea/15272/). It also says that this is not a feature so... I don't really know how you rid yourself of the root password prompt unless you did some hack that you didn't post?? I hope that helps.

Thank for your help.
When using package manager, there is no options to rememmer the password (Image 1) , but there will be if you mount partitions using menu Places or Nautilus ( Image 2 - Option: Remember Authorization - I checked it before).  I don't install any password manager and hack anything. Now everyone who uses my Ubuntu ( with my system account,of course) can add/remove programs by using Synaptic without being prompted to enter password. They can also mount my data partitions without password. I want to get rid of them. 

Don't tell me that don't allow others to use my computer with my account. I can't do this all the time.

All I want is to be prompted password whenever using Synaptic, mounting partition or other administrative tasks. Please help me!
Image 1:
[IMG]http://img512.imageshack.us/img512/1150/ubuntu20090822174522.png[/IMG]
Image 2:
[img]http://img341.imageshack.us/img341/5826/ubuntu20090822174947.png[/img]

---

### Post by Operan on 2009-08-22
I've solved this problem. Just run : polkit-gnome-authorization and revoke my account from related items. Thank for your helps.

---

