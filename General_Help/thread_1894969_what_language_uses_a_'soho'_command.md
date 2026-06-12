---
title: "what language uses a 'soho' command?"
date: 2011-12-13
forum: General Help
---

### Post by smcrossman on 2011-12-13
I'm trying to get mapped drive access to shares on my NAS.  The program that comes with it (Win, MAC & some linux) installs but its not really working.  When I go into the file I"m seeing a command that I don't recognize (of course I am NOT a programmer) and I'm wondering if that might be part of the problem.

```
#!/bin/sh


curdir=`dirname "$0"`
soho_dist_lib=./lib
soho_selinux_lib=./lib_se
soho_dist_bin=IomegaStorageManager-bin
para="$@"

isKDE()
{
    if [ "$DESKTOP_SESSION" = "kde" ]
    then 
        return 1
    else 
        if [ "$KDE_SESSION_UID" != "" ]
        then 
            return 1
        else 
            return 0
        fi
    fi
```

I've searched but haven't found any kind of information on 'soho'  Any chance that changing this one word throughout the files to a command that Ubuntu recognizes will make my life easier? 

Thanks in advance for sharing any knowledge!

---

### Post by bab1 on 2011-12-13
> **smcrossman said:**
> I'm trying to get mapped drive access to shares on my NAS.  The program that comes with it (Win, MAC & some linux) installs but its not really working.  When I go into the file I"m seeing a command that I don't recognize (of course I am NOT a programmer) and I'm wondering if that might be part of the problem.

```
#!/bin/sh


curdir=`dirname "$0"`
soho_dist_lib=./lib
soho_selinux_lib=./lib_se
soho_dist_bin=IomegaStorageManager-bin
para="$@"

isKDE()
{
    if [ "$DESKTOP_SESSION" = "kde" ]
    then 
        return 1
    else 
        if [ "$KDE_SESSION_UID" != "" ]
        then 
            return 1
        else 
            return 0
        fi
    fi
```

I've searched but haven't found any kind of information on 'soho'  Any chance that changing this one word throughout the files to a command that Ubuntu recognizes will make my life easier? 

Thanks in advance for sharing any knowledge!

There is no command *soho*. 

The code that you are referring to is variable substitution.  The writer of the code is giving a name to a variable like this```
NAME_OF_VARIABLE=some_data
``` 

Read it from right to left like this:  some_data = NAME_OF_VARIABLE

I'll bet the writer is using the term as in "**S**mall **O**ffice - **H**ome **O**ffice = SOHO

---

