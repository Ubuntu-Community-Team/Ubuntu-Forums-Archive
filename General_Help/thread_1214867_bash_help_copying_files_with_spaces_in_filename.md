---
title: "bash help: copying files with spaces in filename"
date: 2009-07-16
forum: General Help
---

### Post by stepper on 2009-07-16
I'm trying to get an Amarok art cover file and place it in the home folder with the name cover.jpg
The script works for a filename with no spaces in the directory and the file itself. How I can copy a file with spaces in it? 

My Script
```

#!/bin/bash

qdbus org.kde.amarok /Player GetMetadata | grep arturl | cut -f3- -d"/" > cover.txt
picture=`php -r '$t=file_get_contents("cover.txt");echo utf8_encode(urldecode(urldecode($t)));'` #encode to utf8
if [ -e `qdbus org.kde.amarok /Player GetMetadata | grep arturl | cut -f3- -d"/"` ] #checks for artfile
	then  cp "$picture"  /home/stepper/cover.jpg
	else cp /home/stepper/disk.jpg /home/stepper/cover.jpg
fi

exit 0

```

For example a file like "/media/music/RastaStar/Dubmixes/folder.jpg" will work but not "/media/music/Rasta Star/Dubmixes/folder.jpg"

---

### Post by roccivic on 2009-07-16
I had problems with spaces in bash recently, this may be of help:
[http://ubuntuforums.org/showthread.php?t=1213721](http://ubuntuforums.org/showthread.php?t=1213721)

---

### Post by stepper on 2009-07-16
I think I got it working. Anybody with amarok can test on their side.:)

The new script:
```

#!/bin/bash

qdbus org.kde.amarok /Player GetMetadata | grep arturl | cut -f3- -d"/" > cover.txt
picture=`php -r '$t=file_get_contents("cover.txt");echo utf8_encode(urldecode(urldecode($t)));'` #encode to utf8
if [ -z "$picture" ] #checks for artfile
then	cp /home/stepper/disk.jpg /home/stepper/cover.jpg
	else echo "$picture" |xargs -I{} cp "{}" ~/cover.jpg
fi

exit 0

```
I use this script to generate an image to use in conky with amarok.

---

