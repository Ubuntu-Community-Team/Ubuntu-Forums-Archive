---
title: "Directory possibly corrupted"
date: 2010-08-16
forum: General Help
---

### Post by cforbes on 2010-08-16
A directory on my desktop has recently become inaccessible. The error message that is given when I attempt to open the directory is as follows:

Could not display "nikki stuff",
The file is of unknown type. 

I brought up a terminal and did an ls -l on the directory, which produced the following:

-rwxrwxrwx 1 nikki nikki    314 2010-07-26 19:16 nikkis%20stuff.desktop

Unfortunately, the computer is not mine, so I do not know much more about how this happened. 

Please Help.

Thanks

---

### Post by Smart Viking on 2010-08-16
Try this:

```
file nikkis%20stuff.desktop
```
(if that is the name of the file)

It looks like it is only a link, not an directory? :)

---

### Post by cforbes on 2010-08-16
That changed the contents of the file to:

#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Name=nikkis stuff
Comment=Open '/home/nikki/Desktop/nikkis stuff'
Icon=inode-directory
Name[en_US]=nikkis stuff
Comment[en_US]=Open '/home/nikki/Desktop/nikkis stuff'
Icon[en_US]=inode-directory
URL=file:///home/nikki/Desktop/nikkis%20stuff
Type=Link

Looks like you were right it was a link, but it doesn't show where and it no longer functions as a link. Can this be fixed?

---

