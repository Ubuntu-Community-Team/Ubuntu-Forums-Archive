---
title: "Youtube Videos Not Working Right"
date: 2010-07-24
forum: General Help
---

### Post by thetaximan43 on 2010-07-24
I am relatively new the linux. I recently installed the latest flash for linux so i can watch youtube videos. the videos play like they should, but none of the flash buttons work - and it seems to be only Youtube videos (other websites work fine). I have tried to find a solution, but it seems that most of the issues were from older versions of ubuntu (8.4 or something) and i wasn't sure if that would work on my version.

I am using the 64 bit version of Ubuntu, if that helps anyone out there.

---

### Post by Rustybolts on 2010-07-24
Are you using compiz ? if so try turning it off.

---

### Post by thetaximan43 on 2010-07-24
> **Rustybolts said:**
> Are you using compiz ? if so try turning it off.
Tried that out...

...but it didn't work.

---

### Post by thetaximan43 on 2010-07-24
I also just noticed that it is only videos that still load up using the old button system. Does anyone know why some videos are still using the old system? I guess thats more of a Youtube support question. :P

---

### Post by lovinglinux on 2010-07-24
This usually happens when you are using the 32bit plugin on a 64bit system.

To fix that you need to edit the npviewer file. Open it with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

---

### Post by thetaximan43 on 2010-07-24
That worked perfect.

thanks LovingLinux :)

---

### Post by lovinglinux on 2010-07-24
> **thetaximan43 said:**
> That worked perfect.

thanks LovingLinux :)

You are welcome.

---

### Post by JaSoN369 on 2010-07-25
thanks lovinglinux worked for me also.

---

