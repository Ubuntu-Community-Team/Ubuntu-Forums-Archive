---
title: "won't let me delete files and folders in GUI"
date: 2006-04-01
forum: General Help
---

### Post by lordjeff on 2006-04-01
I had 3 HDDs in the machine that I installed ubuntu on to.  Previously, it had Xandros on it.  The file systems are ext3.  I seem to have some permissions on these disks that don't have an owner.  The result of which is that I can't delete them or put new stuff into those folders using the GUI.  Help!  I'm a noob when it comes to command line stuff.  I just need to either reset all permissions throughout the drives to the current user or delete them completely so the drive is wide open (preferred).  Any help is appreciated.  

](*,) Thanks in advance, I know that i'm a knob. ;)

---

### Post by Gnobody on 2006-04-01
[quote=lordjeff]I had 3 HDDs in the machine that I installed ubuntu on to.  Previously, it had Xandros on it.  The file systems are ext3.  I seem to have some permissions on these disks that don't have an owner.  The result of which is that I can't delete them or put new stuff into those folders using the GUI.  Help!  I'm a noob when it comes to command line stuff.  I just need to either reset all permissions throughout the drives to the current user or delete them completely so the drive is wide open (preferred).  Any help is appreciated.  

](*,) Thanks in advance, I know that i'm a knob. ;)[/quote]


sudo chown -R yourusername /media/whateverpartitionitis && sudo chmod -R 777 /media/whateverpartitionitis

---

### Post by adamkane on 2006-04-01
You can use the find command to find files and update their permission:
[http://ubuntuforums.org/showthread.php?t=16916]("http://ubuntuforums.org/showthread.php?t=16916")

This thread give a couple of examples. If you want to specify the directory that you want to make read/write:

```

find /mystuff -type f -exec chmod 755 {} \;

``` 
```

find /mystuff -type f -exec chown myname {} \;

``` 
```

 find /mystuff -type f -exec chown mygroup {} \;
 
``` 
Test before you run the command everywhere!

More info:
-type f - files
-type d - directories
chmod - change read/write/execute
chown - change owner
chgrp - change group

Don't use 777. Sheez louise!

---

