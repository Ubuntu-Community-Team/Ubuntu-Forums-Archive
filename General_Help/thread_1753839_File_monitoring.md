---
title: "File monitoring?"
date: 2011-05-09
forum: General Help
---

### Post by Ranko Kohime on 2011-05-09
Anyone know of a program that can monitor changes to files?

I've had an issue for a while now where files will simply disappear.  Specifically, FLAC files that are loaded into Rhythmbox.  Once I've found the files in the Trash bin, but I've just noticed several that appear to have been missing for some time, as they were not in the Trash.

Basically, I'd like something that will log the non-read activities of a given directory or directories.

Thanks for any suggestions.  :)

---

### Post by dragonfly41 on 2011-05-09
As an ex windows user I haven't seen anything in ubuntu to equate with windows utilities in [www.sysinternals.com](www.sysinternals.com) ... such as filemon

but a quick search brought up inotify, iwatch and fam .. perhaps look them up .. I haven't tried them

[http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html?S_TACT=105AGX59&S_CMP=grsite-lnxw9611&ca=dgr-lnxw961Ubuntu-inotify](http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html?S_TACT=105AGX59&S_CMP=grsite-lnxw9611&ca=dgr-lnxw961Ubuntu-inotify)

---

### Post by Ranko Kohime on 2011-05-09
> **dragonfly41 said:**
> As an ex windows user I haven't seen anything in ubuntu to equate with windows utilities in [www.sysinternals.com](www.sysinternals.com) ... such as filemon

but a quick search brought up inotify, iwatch and fam .. perhaps look them up .. I haven't tried them

[http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html?S_TACT=105AGX59&S_CMP=grsite-lnxw9611&ca=dgr-lnxw961Ubuntu-inotify](http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html?S_TACT=105AGX59&S_CMP=grsite-lnxw9611&ca=dgr-lnxw961Ubuntu-inotify)
I saw fam, but it did not appear to be a homogeneous program.  (I'd like to avoid scripting this, if I could), and, for whatever reason, installing from the repos requires the removal of half the Ubuntu GUI.  :confused:

As for the other 2, I'll have a look at them.  :)

---

### Post by erind on 2011-05-09
I usually use **inotifywait** ( from **inotify-tools** package ) for such tasks, and it just works great, and not much scripting is involved to use it. Here goes an example of *inotifywait* usage taken from its man pages:
[http://linux.die.net/man/1/inotifywait](http://linux.die.net/man/1/inotifywait)

```
# A short shell script to efficiently wait for httpd-related log messages and do something appropriate.

#!/bin/sh
while inotifywait -e modify /var/log/messages; do
  if tail -n1 /var/log/messages | grep httpd; then
    kdialog --msgbox "Apache needs love!"
  fi
done
```How to install it and some other examples here: [https://github.com/rvoicilas/inotify-tools/wiki/](https://github.com/rvoicilas/inotify-tools/wiki/)

---

### Post by kaspar_silas on 2011-05-09
Or if you want to avoid installing more packages and can deal with a little more scripting. You can do it very easily like this.


```
#! /bin/sh
folder="PATH_TO_YOUR_FOLDER_TO_MONITOR"

#This lines measures the folder size
old=`du -s $folder | awk '{print $1}'`
while [ 1 = 1 ];
do
  new=`du -s $folder | awk '{print $1}'`
  #If different alert user with Desktop file
  if [ $old -ne $new ] ; then 
    echo "folder Size Change at `date`">>~/Desktop/NOTIFICATION
  fi
  old=$new
  sleep 3;
done
```

---

