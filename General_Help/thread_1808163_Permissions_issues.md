---
title: "Permissions issues"
date: 2011-07-20
forum: General Help
---

### Post by Alistair George on 2011-07-20
I suspect permissions as this seems to be error that I am getting with apps such as krusader, k3b etc typical report as below.
However under Control/Users have set my account as administrator so surely the permissions should be already granted.
I can run the softwares under sudo eg sudo k3b so why cant the permissions be correct if I am administrator?

Thanks vm for any help that can be suggested.
Alistair

trying to create local folder /home/alistair/.kde/cache-alsmain: Permission denied
drkonqi(3531)/kdeui (KIconLoader) KSharedDataCache::Private::mapSharedMemory: Failed to establish shared memory mapping, will fallback to private memory -- memory usage will increase
trying to create local folder /home/alistair/.kde/cache-alsmain: Permission denied
trying to create local folder /home/alistair/.kde/cache-alsmain: Permission denied
trying to create local folder /home/alistair/.kde/cache-alsmain: Permission denied
trying to create local folder /home/alistair/.kde/cache-alsmain: Permission denied
trying to create local folder /home/alistair/.kde/tmp-alsmain: Permission denied
trying to create local folder /home/alistair/.kde/tmp-alsmain: Permission denied
trying to create local folder /home/alistair/.kde/tmp-alsmain: Permission denied
trying to create local folder /home/alistair/.kde/tmp-alsmain: Permission denied
trying to create local folder /home/alistair/.kde/tmp-alsmain: Permission denied
drkonqi(3531): Failed to lock file "/home/alistair/.kde/cache-alsmain/kpc/kde-icon-cache.lock" , last result = 2
drkonqi(3531): Couldn't create index file "/home/alistair/.kde/cache-alsmain/kpc/kde-icon-cache.index"
QFile::remove: Empty or null file name
Fatal Error: Accessed global static 'KGlobalPrivate *globalData()' after destruction. Defined at ../../kdecore/kernel/kglobal.cpp:127
KCrash: Application 'drkonqi' crashing...
Fatal Error: Accessed global static 'KGlobalPrivate *globalData()' after destruction. Defined at ../../kdecore/kernel/kglobal.cpp:127
Unable to start Dr. Konqi

---

### Post by Wim Sturkenboom on 2011-07-20
> **Alistair George said:**
> 
However under Control/Users have set my account as administrator so surely the permissions should be already granted.
No, that only means that the user is added to the sudoers file and therefore can use sudo.

PS No solution to your problem ;)

---

### Post by Alistair George on 2011-07-20
> **Wim Sturkenboom said:**
> No, that only means that the user is added to the sudoers file and therefore can use sudo.

PS No solution to your problem ;)

Oh, ok thanks for that; what command should I use to get to administer permissions as root? Thanks.

---

### Post by LowSky on 2011-07-20
> **Wim Sturkenboom said:**
> 
PS No solution to your problem ;)

Liar!


Go to your home folder and create the files it is trying to create in the correct spots, make sure the permissions are correct, they should NOT be root or sudo but associated with your user name

If using Gnome, open nautilus, right click on a file in your home folder go to properties at the bottom, then click on the permissions tab owner and group should both be in your name, if they are not change it to be so. If you can't you will need to open nautilus as root like so
open terminal:
```
gksu nautilus
```

I've attached my document properties as a example

---

### Post by Alistair George on 2011-07-20
> **LowSky said:**
> Liar!


Go to your home folder and create the files it is trying to create in the correct spots, make sure the permissions are correct, they should NOT be root or sudo but associated with your user name

If using Gnome, open nautilus, right click on a file in your home folder go to properties at the bottom, then click on the permissions tab owner and group should both be in your name, if 
```
gksu nautilus
```

I've attached my document properties as a example

Hi I did this and clicked 'Apply permissions to enclosed' it does not do this! Something weird going on as I have to go inside the lower folder and cant even highlight all files as permissions are all root as both cases. Individually, I can change, but as a group I cant.
Thanks. Alistair.

---

