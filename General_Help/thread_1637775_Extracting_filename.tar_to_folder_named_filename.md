---
title: "Extracting filename.tar to folder named filename"
date: 2010-12-04
forum: General Help
---

### Post by v1rati on 2010-12-04
Hi. I was wondering if there was a way to extract a .tar file to a folder named as the .tar file.
When I download a .tar.bz2 file, and do "Extract Here". It usually extracts all the 15+ files into my Downloads folder.

I know that I can manually do it by going into Archive Manager and doing extract, but I was wondering if there's an automated way to do it since most filenames are complex like "fms-linux-x86-64-bin-0.3.53.tar.bz2".

Thanks.

---

### Post by asmoore82 on 2010-12-04
Most tar files I come across do this already.
(mostly sources from sourceforge, launchpad, or linux kernel)

So I think the real problem is with who packaged your tar files.

You could save a quick bash script and use it from "open with"

```
[COLOR="Blue"]#!/bin/bash[/COLOR]

case "$1" in
    *.tar.gz )
        extract="z"
        folder="${1%.tar.gz}"
        ;;
    *.tgz )
        extract="z"
        folder="${1%.tgz}"
        ;;
    *.tar.bz2 )
        extract="j"
        folder="${1%.tar.bz2}"
        ;;
    *.tbz )
        extract="j"
        folder="${1%.tbz}"
        ;;
    * )
        echo "ERROR: Unknown Archive type." 1>&2
        exit 1
        ;;
esac

extract="-${extract}xvf"

[COLOR="Purple"]mkdir "$folder"[/COLOR]
tar "$extract" "$1" -C "$folder"

[COLOR="Blue"]#End of File[/COLOR]
```

---

### Post by v1rati on 2010-12-05
Yeah. That's exactly why I wanted this was for the finicky packaging. I wanted to make a shell script to run with Open With, but I don't know the first thing about Bash Programming. :\ So thanks a lot. :)

I made a (shoddy) python script to do that, but it didn't work with Open With. I'll post it in case someone stumbles across this thread:
```

#! /usr/bin/env python

import sys
import os

if len(sys.argv) == 0 or len(sys.argv) > 1:
    tarname = sys.argv[1]
##    # Strip path of quotes
##    if tarname[0] == r"'" and tarname[len(tarname)-1] == r"'":
##        path = tarname[1:len(tarname)-2]
##        print path
    extIndex = tarname.find('.tar')
    folder = tarname[0:extIndex]
    if tarname.find('.gz') != -1:
        os.popen("mkdir " + folder)
        os.popen("tar --verbose -zxvf " + sys.argv[1] + " -C " + folder)
    elif tarname.find('.bz2') != -1:
        os.popen("mkdir " + folder)
        os.popen("tar --verbose -jxvf " + sys.argv[1] + " -C " + folder)
    else:
        print 'Input file is neither .gz or .bz2'
else:
    print('Invalid number of args')


```

---

### Post by v1rati on 2010-12-05
I tried using your shell script, except it's spitting out this error:
```
$ ./tarfolder.sh FahMon-2.3.99.1.tar.bz2 
tar: FahMon-2.3.99.1: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now

```

---

### Post by asmoore82 on 2010-12-05
oops, must need a `mkdir` ... I thought tar would make it.

I'll edit in the fix above.

---

### Post by v1rati on 2010-12-05
Awesome. Thanks again, mate. :)

---

