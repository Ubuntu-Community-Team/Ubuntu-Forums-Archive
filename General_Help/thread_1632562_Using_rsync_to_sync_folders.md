---
title: "Using rsync to sync folders"
date: 2010-11-28
forum: General Help
---

### Post by rmcellig on 2010-11-28
OK, here is the test code I am using:

rsync -acrv /home/randy/Documents /media/USB2/testbackup

What should I put in the code so that when I delete something in the Documents folder, it will also be deleted in the testbackup folder when I perform a sync.

How can I have it so the code will check if USB2 is available, if it is, do the sync, if not, do nothing.

---

### Post by mikewhatever on 2010-11-28
rsync -acv --delete /home/randy/Documents/ /media/USB2/testbackup/

I've taken the liberty to remove '-r', since '-a' already contains it. (-a = -rlptgoD according to man rsync)

As for checking for USB2, you'll need to put it all into a script (say, rsync-script), make it executable, then run ./rsync-script:

```

#!/bin/bash
#check if the dir exists
if [ -d /media/USB2 ]
then
rsync -acv --delete /home/randy/Documents/ /media/USB2/testbackup/
else
echo "USB2 is not connected, exiting..."
fi

```

---

