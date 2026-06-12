---
title: "help with Kate -- cannot configure due to permission issues (I guess)"
date: 2011-09-05
forum: General Help
---

### Post by harlequin_ on 2011-09-05
(important edit at the very end)

Hi everyone,

I'm using ubuntu 11.04 with Kate (version 3.6.2). Until yesterday I guess everything was fine with it (it's my default text editor). Now today I realized that Kate does not remember my choice for not displaying tips at the startupcrashes when I try to save an open file or open a file. "New" and "Close" work properly, for instance.

```

alimay@alimay-laptop:~$ kate
trying to create local folder /home/alimay/.kde/cache-alimay-laptop: Permission denied
kate(8086)/kdeui (KIconLoader) KSharedDataCache::Private::mapSharedMemory: Failed to establish shared memory mapping, will fallback to private memory -- memory usage will increase 
trying to create local folder /home/alimay/.kde/cache-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/cache-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/cache-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/cache-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
kate(8086): Failed to lock file "/home/alimay/.kde/cache-alimay-laptop/kpc/kde-icon-cache.lock" , last result = 2 
kate(8086): Couldn't create index file "/home/alimay/.kde/cache-alimay-laptop/kpc/kde-icon-cache.index" 
QFile::remove: Empty or null file name
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/socket-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/alimay/.kde/socket-alimay-laptop/kdeinit4__0'
trying to create local folder /home/alimay/.kde/cache-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/share: Permission denied
QFile::remove: Empty or null file name
QFile::remove: Empty or null file name
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/socket-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/tmp-alimay-laptop: Permission denied
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/alimay/.kde/socket-alimay-laptop/kdeinit4__0'
trying to create local folder /home/alimay/.kde/cache-alimay-laptop: Permission denied
trying to create local folder /home/alimay/.kde/share: Permission denied
kate(8086): No ksycoca4 database available! 

kate(8086)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "KTextEditor/Plugin"  not found 
trying to create local folder /home/alimay/.kde/share: Permission denied
kate(8086): No ksycoca4 database available! 

kate(8086)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "Kate/Plugin"  not found 
trying to create local folder /home/alimay/.kde/share: Permission denied
trying to create local folder /home/alimay/.kde/share: Permission denied

```


Big thanks!

---

### Post by harlequin_ on 2011-09-05
anyone?

---

### Post by harlequin_ on 2011-09-06
bump

---

### Post by crumple on 2011-09-13
been having a similar problem using startx as a non-root user rather than kate, here's my hotfix so i can finally go to bed now

sudo dbus-launch /usr/bin/dolphin 

navigate to the /home/USERNAME/.local/share folder
-->don't forget the period right before local

right click on the folder and select properties, then click the permissions tab

change all permissions to can view and modify content

under where it says ownership, select the option to apply changes to all subfolders and contents

did a startx as a normal user and booted right up, but the startup apps all needed to be root verified, so it's prob something to do with adding the user to the root group but idk. will update if anything new happens


tl;dr check your user permissions  in /home/USERNAME/.local

---

### Post by SeijiSensei on 2011-09-13
```

cd /home
sudo chown alimay.alimay alimay -R

```

Something is wrong with permissions in your home directory.  The commands above will reset the ownership of all files in /home/alimay to the alimay user and group.  (The "-R" switch tells chown to recurse through all subdirectories.) See if that helps.

---

### Post by harlequin_ on 2011-09-13
> **SeijiSensei said:**
> ```

cd /home
sudo chown alimay.alimay alimay -R

```Something is wrong with permissions in your home directory.  The commands above will reset the ownership of all files in /home/alimay to the alimay user and group.  (The "-R" switch tells chown to recurse through all subdirectories.) See if that helps.

Indeed, it was about permissions. It is fixed now, but thanks for the replies.

---

