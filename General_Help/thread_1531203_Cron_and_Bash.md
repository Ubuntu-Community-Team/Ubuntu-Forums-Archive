---
title: "Cron and Bash"
date: 2010-07-14
forum: General Help
---

### Post by Cavs23 on 2010-07-14
So I have this script that I made that will back my system up and it deletes copies that are older than 10 weeks. I can run this script through my terminal and it works a-okay. But when I put it into cron it copies about 500K worth of stuff then when I open it to see what caused it to stop.
This comes up.

```

tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

```

My script.
```

#!/bin/bash          

NameCheck="`date --date='70 days ago' +%F`-Backup.tgz"
Location="/media/7E98E6F798E6AD39/Backups/"
Name="`date +%F`-Backup"

if [ -f "$Location$NameCheck" ]
then
rm "$Location$NameCheck"
fi

cd /
tar cvpzf "$Location$Name.tgz" --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/home/ron/.wine /

```

I have chmodded both the script and the destination.

---

### Post by Muttley99 on 2010-07-14
Carriage return the end of your script!

---

### Post by SciFi-Bob on 2010-07-14
My experience is that tar sometimes removes the starting slash from several options.
Sometimes it tells you, but not always.
If the current directory of the process is / (root), then it should be sufficient to use this:

--exclude=proc --exclude=lost+found

without the starting slash.

Edit: But then again, it should not work when started manually either..
Most of my problems running scripts in cron, has to do with the environment being different.. Could it be that you need a path setting in your script?

---

### Post by DaithiF on 2010-07-14
Hi,
remove the verbose (v) flag from tar.  Too much stdout output will cause a cron job to fail.

---

### Post by Cavs23 on 2010-07-14
Thank you Daith that did the trick.

---

