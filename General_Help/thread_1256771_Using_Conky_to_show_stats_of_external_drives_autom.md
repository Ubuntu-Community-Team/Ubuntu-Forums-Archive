---
title: "Using Conky to show stats of external drives automatically"
date: 2009-09-03
forum: General Help
---

### Post by lian1238 on 2009-09-03
Hi, I've a python script which detects external drives mounted in /media/ and outputs the conky code to show some stats.

```

import os # for popen

global shown # to show the heading only once
shown = False

def showHeading():
    global shown
    if not shown:
        print '${font Aerial:style=Bold:pixelsize=12}External Drive${font Snap.se:size=8}'
        shown = True

def getDev(mount):
"""Gets the device of a mounted partition"""
    return os.popen('mount | grep /media/'+mount).read().strip().split(' ')[0]

def getMountList():
    # get a list of folders in /media/
    # skip cdrom folders
    ls = os.popen("ls /media/ | grep -v cdrom").read().strip().split('\n')
    for item in ls:
        showHeading()
        print '/media/'+item
        print 'Write${goto 158}Read'
        print '${diskiograph_write normal '+getDev(item),
        print '10, 150 ff0000 ff0000}',
        print '${diskiograph_read normal '+getDev(item),
        print '10, 150 00ff00 00ff00}'
        print '${fs_bar 3,180','/media/'+item+'/}',
        print '${fs_free /media/'+item+'/}','/',
        print '${fs_size /media/'+item+'/}'

getMountList()

```It works for about 10 seconds. Then conky reports this:
```

Conky: too many diskio stats
Conky: too many diskio stats

```The above two lines show up every 1 second. I guess the script is being run many times?

---

### Post by lian1238 on 2009-09-04
Bump.

---

