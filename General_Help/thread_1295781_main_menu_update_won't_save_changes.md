---
title: "main menu update won't save changes"
date: 2009-10-19
forum: General Help
---

### Post by stans on 2009-10-19
How do I get the Main Menu to retain what I have checked 'on' ?

I did try a couple of chmods from a posting -

find ~/.config/menus -type f -exec chmod 644 {} \;
sudo chown -R $USER:$USER ~/.config

But neither helped.  I recall this problem from a long long time ago but am not sure there was ever a resolution.

I'm running Karmic.

---

### Post by Giblet5 on 2009-10-19
I just had this problem too.

I logged off and flipped to the console via Ctrl-Alt-F1 and logged in to my account.

```
sudo find .config -type d -exec chmod 750 {} \; -exec chown `username`:`username` {} \;
sudo find .config -type f -exec chmod 640 {} \; -exec chown `username`:`username` {} \;
```

I flipped back to X via Ctrl-Alt-F7 and I logged back in.

That fixed it. For me. That time. For now.

---

### Post by stans on 2009-10-20
Thank You Giblet5... because I am so spoiled with cut/paste I'll create a file containing these commands to execute.

---

### Post by Giblet5 on 2009-10-20
> **stans said:**
> Thank You Giblet5... because I am so spoiled with cut/paste I'll create a file containing these commands to execute.

A better script for that:
```
#!/bin/bash

## Invent a name
PRG=`basename $0`

## make sure there are proper arguments
if [ "$1" -eq "" ] ; then
    echo "$PRG -
Fix ownership/perms on one or more directories.
Recursively sets mode rwxr-x--- on directory files, rw-r----- on
regular files, to the named directories, inclusively."
    echo "Usage: $PRG dir1 dir2 ... dirN"
    exit 1
fi

## Do the work
while [ "$1" -neq "" ]
do
    sudo find "$1" -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
    ## Stop if it fails
    if [ $? -neq 0 ] ; then
        echo "$PRG: Exiting on error while processing $1"
        break
    fi
    sudo find "$1" -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
    if [ $? -neq 0 ] ; then
        echo "$PRG: Exiting on error while processing $1"
        break
    fi
    shift
done

exit $?
```

---

### Post by stans on 2009-10-20
That's quite elegant. Thanks again for your assistance.

---

