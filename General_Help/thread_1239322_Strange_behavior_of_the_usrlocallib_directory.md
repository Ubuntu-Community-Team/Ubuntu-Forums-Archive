---
title: "Strange behavior of the /usr/local/lib directory"
date: 2009-08-13
forum: General Help
---

### Post by PsyCowboy on 2009-08-13
Hi all,

As explained in the title, I have troubles to understand the behavior of the /usr/local/lib directory (or maybe the "locate" behavior). I'm have installed a new version of the Ogre library and there is something strange because when I type:

$ locate OgreMain | grep /usr/local/lib
/usr/local/lib/libOgreMain-1.6.1.so
/usr/local/lib/libOgreMain.la
/usr/local/lib/libOgreMain.so

$ ls /usr/local/lib | grep OgreMain
libOgreMain-1.6.3.so
libOgreMain.la
libOgreMain.so

](*,)
How explain the difference between the versions? Is it because the locate's database is not updated?

(My life doesn't depends on the answer. But I just want to understand better my system...)
Thanks

---

### Post by DaithiF on 2009-08-13
Hi,
yes, probably.  the locate database is typically updated daily via the cron/anacron mechanism.  depending on when that runs you may not see up-to-date results.

you can manually run the updatedb command to verify:
```
sudo updatedb
```

---

### Post by PsyCowboy on 2009-08-13
Oho,

thank you for your time, that's it! \\:D/

I was close to the solution...

---

