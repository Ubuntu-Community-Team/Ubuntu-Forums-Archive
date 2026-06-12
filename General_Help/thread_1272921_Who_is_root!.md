---
title: "Who is root?!"
date: 2009-09-22
forum: General Help
---

### Post by Necromantis on 2009-09-22
I have a question:
Who is root?

What I am trying to ask is: on my computer, root has access to everything - so, if I store some documents on a usb HD and set root as owner; does that mean that my PC root account has access or does that mean that every ubuntu / linux PCs root account has access? :confused:

Thanks

---

### Post by credobyte on 2009-09-22
*He* can see ( change/move/delete/etc. ) everything :P

---

### Post by FreezWay on 2009-09-22
a superadmin....




-I AM ROOT!!!!!!!!! (youtube meme)

---

### Post by cybergalvez on 2009-09-22
> **Necromantis said:**
> I have a question:
Who is root?

What I am trying to ask is: on my computer, root has access to everything - so, if I store some documents on a usb HD and set root as owner; does that mean that my PC root account has access or does that mean that every ubuntu / linux PCs root account has access? :confused:

Thanks

The short answer is yes, every ubutnu /  linux root account has access to your root files.

---

### Post by Iowan on 2009-09-22
Eventually, someone will post [this]("https://help.ubuntu.com/community/RootSudo") link...

---

### Post by bab1 on 2009-09-22
> **credobyte said:**
> *He* can see ( change/move/delete/etc. ) everything :P

And what if *He* is She*?

Seriously, the account *root* is always number 0.  See:```
getent passwd|grep root
root:x:0:0:root:/root:/bin/bash

```Any files owned by the account 0 are owned by the root account of the system that can see (mounted) the files.

---

### Post by t0p on 2009-09-22
> **cybergalvez said:**
> The short answer is yes, every ubutnu /  linux root account has access to your root files.

Indeed.  For instance, I'm root on my computer.  Which means I have root access on all Linux computers.  This is why Linux is so insecure.

:p

---

### Post by bab1 on 2009-09-22
> **t0p said:**
> Indeed.  For instance, I'm root on my computer.  Which means I have root access on all Linux computers.  This is why Linux is so insecure.

:p

Why is it insecure because you have root access on YOUR linux hosts?  

You certainly do not have root access on my Linux hosts.

---

### Post by akakingess on 2009-09-22
> **bab1 said:**
> Why is it insecure because you have root access on YOUR linux hosts?  

You certainly do not have root access on my Linux hosts.

+1, there is a root per machine, but that doesn't mean that root on my server could see root files on a client machine, at least that is my understanding.

---

### Post by louieb on 2009-09-22
> **t0p said:**
> Indeed.  For instance, I'm root on my computer.  Which means I have root access on all Linux computers.  This is why Linux is so insecure.

:p
:lolflag:Been drinking again? Or just feeling mischievous?

---

### Post by doas777 on 2009-09-22
ok op, if your still paying attention, 
the root is the system admin account, but noone is that user. the root account in ubuntu is disabled so no one can login into it (unless they first enable it). it's much safer 

instead, as Iowan pointed out, when you need admin access in ubuntu, you impersonate the root account by using sudo or gksu in front of any given command.

---

### Post by Necromantis on 2009-09-23
> **bab1 said:**
> Why is it insecure because you have root access on YOUR linux hosts?  

You certainly do not have root access on my Linux hosts.

If I take your hard drive(s) and connect it/them to my PC - start ubuntu , mount the drives , go to console:
sudo chown -R root:root *foldername*

Then I would have access to all your files, no?

Is there no way to activate some kind of security to protect the data against this kind of action ?

---

### Post by badger_fruit on 2009-09-23
> **Necromantis said:**
> Who is root?

Root is the SUPER USER.

Neither male or female, instead a legendary multi-sex warrior which has full control of every file, folder and symlink in your file-system. Use with care and root will be a powerful ally; abuse it and your system will lie in a burning heap, the cold, evil stare of root will driving you insane.

In linux when you're root, you are not asked "are you sure", even your system is afraid to question the almighty root.


cybergalvez - your reply "every ubutnu /  linux root account has access to your root files" is sort of right, sort of wrong.

On every *nix machine in the world there is a default account created - this account is called "root".  Root has FULL control of the filesystem where it is.  For example you may have two computers, both running Ubuntu.  Root account on Computer 1 has NO authority on Computer 2 and likewise, the root account on Computer 2 has no authority on Computer 1.


Necromantis, you go on to say that if you "take your hard drive(s) and connect it/them to my PC - start ubuntu , mount the drives , go to console:  sudo chown -R root:root *foldername*" ... yes your root account would own it and have un-restricted access.

"Is there no way to activate some kind of security to protect the data against this kind of action ?"

What, apart from the owner of the PC saying "get off my HDD"? Yes; the HDD owner encrypts the HDD = no mount = no chown/chgrp = SECURE DATA.

---

### Post by Necromantis on 2009-09-23
> What, apart from the owner of the PC saying "get off my HDD"? Yes; the HDD owner encrypts the HDD = no mount = no chown/chgrp = SECURE DATA.

lol - I'm trying to figure out how to secure the file system from root or other accounts if some **** were to stole my PC :) In my crazy mind linux files were protected by some kind of hidden password within some hidden filestructures.. obviously not the case.

Data encryption is needed then.. I only need part of the files (my files) to be protected, so I'm guessing tcfs is the way to go ?

---

### Post by khelben1979 on 2009-09-23
> **Necromantis said:**
> I have a question:
Who is root?

[root Definition]("http://www.linfo.org/root.html").

---

### Post by abhilashm86 on 2009-09-23
> **t0p said:**
> Indeed.  For instance, I'm root on my computer.  Which means I have root access on all Linux computers.  This is why Linux is so insecure.

:p

please:) be carefull while you say this!! many people will read and confuse:)
each and every computer has its root but different passwords!! that clears everyones doubt, also root is disabled in beginning:) so all happy........

---

### Post by credobyte on 2009-09-23
> **bab1 said:**
> And what if *He* is She*?

Seriously, the account *root* is always number 0.  See:```
getent passwd|grep root
root:x:0:0:root:/root:/bin/bash

```Any files owned by the account 0 are owned by the root account of the system that can see (mounted) the files.

:lolflag:

---

