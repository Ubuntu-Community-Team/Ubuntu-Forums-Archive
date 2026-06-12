---
title: "Help Compiling with GCC"
date: 2010-02-02
forum: General Help
---

### Post by billmanhillman on 2010-02-02
I don't seem to have the sys/proc.h header in /usr/include/. What packages do I need to install to use this header?

---

### Post by ibuclaw on 2010-02-02
That file doesn't exist in any packages, see the below link for details:
[http://packages.ubuntu.com/search?mode=exactfilename&suite=karmic&section=all&arch=any&searchon=contents&keywords=proc.h](http://packages.ubuntu.com/search?mode=exactfilename&suite=karmic&section=all&arch=any&searchon=contents&keywords=proc.h)

What are you trying to compile? Is it for Linux? or another OS?

Regards
Iain

---

### Post by billmanhillman on 2010-02-02
It's for linux based operating systems. Maybe there is an easier way. I'm trying to determine via C code, if a given process id is alive or not. Is that possible?

---

### Post by billmanhillman on 2010-02-02
Here is what I used to detect it. Can this be cleaned up? I'm just starting out programming in C.

```


    char* procPath = "/proc/";
    char pidBuffer[10];
    char pathBuffer[20];
    sprintf(pidBuffer,"%d",pid);
    strcat(pathBuffer,procPath);
    strcat(pathBuffer,pidBuffer);
    DIR *pDir;
    Bool bExists = False;

    pDir = opendir (pathBuffer);

    if (pDir != NULL)
    {
     bExists = True;
     (void) closedir (pDir);
    }
    return bExists;

```

---

