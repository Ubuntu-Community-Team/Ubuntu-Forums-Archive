---
title: "scripting? about backticks"
date: 2011-11-24
forum: General Help
---

### Post by garyed on 2011-11-24
I'm working on a simple backup script where everything is saved & archived in a separate folder named by the date. So I'm putting the date as a variable using backticks. It works OK but I'm wondering if there's an easy alternative way to put the date in a variable. I've heard using backticks are not a good programming technique. Here's what I've got:
```

#/bin/bash
# This is a backup that creates an archive directory named by the date that stores all the previous files before the backup.

read -p "To begin backup press Y", name;
if [ "$name" == "Y" ]; then {
Z=`date`;
mkdir /home/gary/back-back/"$Z";
# This copies all the files to a folder named by the date & time
rsync -av /home/gary/back1/* /home/gary/back-back/"$Z"
rsync -avu /home/gary/back1/* /home/gary/backups
echo Done with backup
}
else {
echo "Something wrong, Backup didn't work correctly"
}
fi


``` 

The backup is only a few MB's but its important stuff that I need for work so I'm trying to be extra cautious.

---

### Post by Vaphell on 2011-11-24
use $() instead as in Z=$( date )

---

### Post by garyed on 2011-11-24
Thanks, that works fine.

---

