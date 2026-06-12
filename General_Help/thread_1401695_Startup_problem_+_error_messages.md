---
title: "Startup problem + error messages"
date: 2010-02-08
forum: General Help
---

### Post by staar2 on 2010-02-08
I am using Kubunutu 9.10 and when i start my ubuntu takes after the ubunutu loading bar to black screen. So it takes about 30 seconds and then gives 3 error messages 

> Configuration file "/home/name/.kde/share/config/knotifyrc" not writeable. Please contact your adm...

Configuration file "/home/name/.kde/share/config/foorc" not writeable. Please contact your adm...

And after that i get very strange non QT style error kstartupconfig4 does not exist or fails. Ther error code is 3.

This all started when my laptop failed to come back from hibernation, so i had to make manual shut down and shut it in. Additional problem is the hard disk is begin encrypted, but i can log in and read them so this should be not the problem.

---

### Post by ajgreeny on 2010-02-08
Try changing the ownership of those two files once you are booted, with ```
sudo chown username:username /home/name/.kde/share/config/knotifyrc
```and the same for the other file.  That should make them yours again, if that was the problem.  If that is still not working try ```
sudo chmod 755 /home/name/.kde/share/config/knotifyrc
```to make them read/write for owner and read only for others, executable for all.

---

### Post by staar2 on 2010-02-08
Ok i tried the last line of command and didnt work, any other approaches ?
Would it possible to delete the folder and recreate it ?

---

### Post by ajgreeny on 2010-02-08
Normally it would be, and you can try, but if the files are not writable they will not be deletable either, unless done as root.  Try doing it in recovery mode if that does not work and you may manage.

If you right click on the files involved and also the folder they are in, look at the properties and permissions tab, and tell us what that says, ie owner, other, root, it may be possible to sort this a bit further.

---

