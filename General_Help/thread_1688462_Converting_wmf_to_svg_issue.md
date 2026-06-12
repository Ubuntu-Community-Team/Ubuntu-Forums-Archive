---
title: "Converting wmf to svg issue"
date: 2011-02-15
forum: General Help
---

### Post by cscj01 on 2011-02-15
I am having an issue with the following command:

```
find . -type f -iname '*.wmf' | while read FILE; do FILENAME="${FILE%.*}"; wmf2svg  --wmf-fontdir=/usr/share/fonts/type1/gsfonts -o ${FILENAME}.svg $FILE; done
```

I get the following message:

```
ERROR: bbuf.c (102): wmf_file_open: unable to open file for reading
```.

This message seems to occur for all wmf files in the directory structure.  I am aware of the bug here: > [https://bugs.launchpad.net/ubuntu/+source/libwmf/+bug/629153]("https://bugs.launchpad.net/ubuntu/+source/libwmf/+bug/629153")
That is why I have added the ```
--wmf-fontdir=/usr/share/type1/gsfonts
``` parameter to the wmf2svg command.

I am at a loss as to why I am getting this message.  I can open the wmf files individually with Inkscape, but there are too many to convert them individually.  Any thoughts would be appreciated.  Thanks.

---

### Post by wormyblackburny on 2011-02-15
Permissions issue possibly? try sudo after the find command?

---

### Post by cscj01 on 2011-02-15
> **wormyblackburny said:**
> Permissions issue possibly? try sudo after the find command?

Well, I tried sudo but received the same message.

However, I did get it to work in an individual directory.  I thought it would be recursive and convert all the images in the subdirectories, but that did not happen.  My current directory when I executed the command did not have any images, but all the subdirectories had them.  By cd'ing to each directory and executing the command, I was able to convert the images.

I think find did act recursively, but read or wmf2svg did not or could not for some reason.  At least that seems to be what the symptoms point to at this time.  I am a novice at this, so I am probably presuming too much.

---

