---
title: "Kile will only start with 'sudo kile'"
date: 2010-10-13
forum: General Help
---

### Post by iclestu on 2010-10-13
Hi great gurus of the Ubuntu world. 

I am a firm novice so please be gentle :-)

I have a rather annoying difficulty with my netbook running 10.10 netbook version...

I have kile installed and it was up and running fine. I was doing something in terminal and wanted to start kile so thought all I had to do was type 'kile' and up it would pop but unfortunately terminal spat out a series of 'permissions' type errors (unfortunately I cannot recall any more specifics than that) and it crashed. I tried running it from the menu icon (where it had ran perfectly previously) but hit the crash screen attached. Ever since, I keep hitting the same crash screen although I can run kile from terminal with "sudo kile".

I have tried simply completely removing kile then re-installing but still hit same difficulty.

Anyone have any ideas?

Also, presumably there is no issue with just running kile from "sudo kile" in the interim as a work around?

Thanks guys, any help would be greatly appreciated.

---

### Post by yeats on 2010-10-13
>  I was doing something in terminal and wanted to start kile so thought all I had to do was type 'kile' and up it would pop but unfortunately terminal spat out a series of 'permissions' type errors (unfortunately I cannot recall any more specifics than that) and it crashed

Are you able to paste the terminal errors you're seeing here (within "CODE" tags)?

---

### Post by iclestu on 2010-10-13
Hi,

Thanks for taking an interest.

I hadn't tried to run it again in terminal (other than as 'sudo kile') as I had thought that was what caused the problem in the firs instance. Have tried it again now and get this:

```
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
kile(6977)/kdeui (KIconLoader) KSharedDataCache::Private::mapSharedMemory: Failed to establish shared memory mapping, will fallback to private memory -- memory usage will increase 
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
kile(6977): Failed to lock file "/home/stewart/.kde/cache-stewart-N130/kpc/kde-icon-cache.lock" , last result = 2 
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
kile(6977): Couldn't create index file "/home/stewart/.kde/cache-stewart-N130/kpc/kde-icon-cache.index" 
QFile::remove: Empty or null file name
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/socket-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/stewart/.kde/socket-stewart-N130/kdeinit4__0'
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
QFile::remove: Empty or null file name
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
QFile::remove: Empty or null file name
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/socket-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/stewart/.kde/socket-stewart-N130/kdeinit4__0'
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
kile(6977): No ksycoca4 database available! 

kile(6977)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "KTextEditor/Plugin"  not found 
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
QFile::remove: Empty or null file name
trying to create local folder /home/stewart/.kde/share: Permission denied
QFile::remove: Empty or null file name
QFile::remove: Empty or null file name
kile(6977): "Unable to save bookmarks in /home/stewart/.kde/share/apps/kfileplaces/bookmarks.xml. Reported error was: Insufficient permissions in target directory.. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive." 

trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/socket-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/stewart/.kde/socket-stewart-N130/kdeinit4__0'
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
kile(6977): No ksycoca4 database available! 

kile(6977): No ksycoca4 database available! 

kile(6977): No ksycoca4 database available! 

kile(6977): No ksycoca4 database available! 

trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/socket-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/stewart/.kde/socket-stewart-N130/kdeinit4__0'
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
kile(6977): No ksycoca4 database available! 

kile(6977)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "ThumbCreator"  not found 
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/socket-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/stewart/.kde/socket-stewart-N130/kdeinit4__0'
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
KCrash: Application 'kile' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/stewart/.kde/socket-stewart-N130/kdeinit4__0
Warning: connect() failed: : Permission denied
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi directly
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
drkonqi(6994)/kdeui (KIconLoader) KSharedDataCache::Private::mapSharedMemory: Failed to establish shared memory mapping, will fallback to private memory -- memory usage will increase 
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/cache-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
trying to create local folder /home/stewart/.kde/tmp-stewart-N130: Permission denied
drkonqi(6994): Failed to lock file "/home/stewart/.kde/cache-stewart-N130/kpc/kde-icon-cache.lock" , last result = 2 
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
drkonqi(6994): Couldn't create index file "/home/stewart/.kde/cache-stewart-N130/kpc/kde-icon-cache.index" 
QFile::remove: Empty or null file name
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied
trying to create local folder /home/stewart/.kde/share: Permission denied

[1]+  Stopped                 kile
stewart@stewart-N130:~$ Fatal Error: Accessed global static 'KGlobalPrivate *globalData()' after destruction. Defined at ../../kdecore/kernel/kglobal.cpp:116
KCrash: Application 'drkonqi' crashing...
Fatal Error: Accessed global static 'KGlobalPrivate *globalData()' after destruction. Defined at ../../kdecore/kernel/kglobal.cpp:116
Unable to start Dr. Konqi

```It looks pretty familiar. I'm pretty sure that was the original messages too.

---

### Post by iclestu on 2010-10-13
sorry folks. I got it.

So silly really. All I had to do was look at that code and have changed the permissions of the folder and subfolders and now alls well. 

No idea how the permissions got changed in first instance tho?!

Ho Hum. Working now and alls well. Thanks for your reply chris and sorry if I wasted your time.

---

### Post by adinov on 2010-11-04
I changed permissions but still get this exact same error!
someone hold my hand and guide me through this.

---

### Post by nike984 on 2010-11-22
try this command on the terminal

```
sudo chmod a+w -R ~/.kde/
```

---

### Post by nutsy.ben on 2011-12-13
Same problem here ..... I got this error message
```
KCrash: Application 'kile' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/nutsyben/.kde/socket-ubuntu/kdeinit4__0

[1]+  Stopped                 kile
nutsyben@ubuntu:~$ QSocketNotifier: Invalid socket 23 and type 'Read', disabling...

```

---

