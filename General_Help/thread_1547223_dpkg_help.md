---
title: "dpkg help"
date: 2010-08-06
forum: General Help
---

### Post by MusicianKool on 2010-08-06
so i cannot install anything because update-info-dir file is missing from /var/lib/dpkg/info/ ..  I've searched for the last day and a half for a way to fix this, but nothing.  can't even update dpkg because of this.  so how do I bypass or fix this so I can install stuff (this is a fresh install of ubuntu 10.04 lts Lucid Lynx).  any help would be great thanks.

---

### Post by WorMzy on 2010-08-06
I don't have that file either, and no problems here.. Can you post the exact error you're getting?

---

### Post by MusicianKool on 2010-08-06
installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ... 
/var/lib/dpkg/info/install-info.postinst: 36: update-info-dir: not found 
dpkg: error processing install-info (--configure): 
 subprocess installed post-installation script returned error exit status 127 
Errors were encountered while processing: 
 install-info 
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ... 
/var/lib/dpkg/info/install-info.postinst: 36: update-info-dir: not found 
dpkg: error processing install-info (--configure): 
 subprocess installed post-installation script returned error exit status 127 

I get this every time, doesn't matter what I try to install or upgrade.

---

### Post by sisco311 on 2010-08-06
Please post the output of:
```
cat /usr/sbin/update-info-dir
```

---

### Post by MusicianKool on 2010-08-06
```

#!/bin/bash
# update-info-dir
# create a dir file from all installed info files
# Copyright 2009 Norbert Preining
# GPLv2

INFODIR=/usr/share/info

set -e

#
# since user's environment is taken over into root account when sudo-ing
# we don't want that one's user LANGUAGE setting changes the messages in
# the dir file. Unset LANGUAGE and reload /etc/environment to get
# the system wide settings. See bug #536476
unset LANGUAGE
if [ -r /etc/environment ] ; then
  . /etc/environment
fi

if [ -n "$1" ] ; then
  INFODIR="$1"
fi

if [ ! -d "$INFODIR" ] ; then
  echo "Not a directory: $INFODIR." >&2
  exit 1
fi

if [ -r "$INFODIR/dir" ] ; then
  rm -f "$INFODIR/dir.old"
  cp $INFODIR/dir $INFODIR/dir.old
fi

# we have to remove the dir file not make ginstall-info being surprised
rm -f "$INFODIR/dir"

errors=0
find "$INFODIR" -type f | while read file ; do
  case $file in
    */dir|*/dir.gz|*/dir.old|*/dir.old.gz|*-[0-9]|*-[0-9].gz|*-[1-9][0-9]|*-[1-9][0-9].gz|*.png)
      # these files are ignored
      continue
      ;;
    *)
      ginstall-info "$file" "$INFODIR/dir" || {
        errors=$[errors+1]
      }
      ;;
  esac
done

if [ $errors -gt 0 ] ; then
  exec >&2
  echo
  echo "Updating the index of info documentation produced $errors errors."
fi

exit 0

# vim:set expandtab tabstop=2: #


```

---

### Post by MusicianKool on 2010-08-06
hmm.  well I guess i can reinstall again and hope that fixes it.

---

### Post by sisco311 on 2010-08-06
Hmmm, did you change sudo's PATH environment variable?

What is the command you run to get the error? Are you logged in as root or you use sudo?

What is the output of:
```
sudo sudo -V | grep \$PATH
```

---

### Post by MusicianKool on 2010-08-06
1. I don't believe so

2. well anything that install's/upgrades something so this will do cause it: 
```

sudo apt-get upgrade

```

3.
```

$ sudo sudo -V | grep \$PATH
Value to override user's $PATH with: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

```

---

### Post by sisco311 on 2010-08-06
Well, as quick and dirty fix you could edit the /var/lib/dpkg/info/install-info.postinst file and replace **update-info-dir** with **/usr/sbin/update-info-dir**.

---

### Post by MusicianKool on 2010-08-06
nope didn't work.

```


Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/var/lib/dpkg/info/install-info.postinst: 36: /usr/sbin/update-info-dir: not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by WorMzy on 2010-08-06
Maybe it's not executable.

What does ```
ls -l /usr/sbin/update-info-dir
``` return?

---

### Post by MusicianKool on 2010-08-06
well, I got it to work.  I redownloaded ubuntu and put it no a usb using ubuntu's startup disk creator (I did it the same way before but through windows - using ubuntu's howto) and reinstalled.  So it might be that the download/install was corrupted.  or there is something funny going on with how windows made the bootable usb stick corrupting the install.   Thank you for your help!

---

