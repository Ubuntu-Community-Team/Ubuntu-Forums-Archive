---
title: "simple script permisions issue"
date: 2012-08-27
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-08-27
```
#!/bin/sh
user="user"
ramFolder="/tmp/$user-firefox"
hddFolder="/home/$user/.mozilla/Cache"
if [ -d "$ramFolder" ]; then
    rsync -rp --delete "$ramFolder/Cache/" "$hddFolder"/
else
    mkdir "$ramFolder"
    chown $user:$user "$ramFolder"
    chmod 700 "$ramFolder"
    sudo -u $user cp -a "$hddFolder" "$ramFolder" &
fi
exit
```
somehow i end up with root owning some files, i think it is rsync doing it
this script is run by rc.local, and at shutdown/reboot
/tmp is a ram disk

---

### Post by dodo3773 on 2012-08-27
> **pqwoerituytrueiwoq said:**
> [CODE]
somehow i end up with root owning some files, i think it is rsync doing it
this script is run by rc.local, and at shutdown/reboot
/tmp is a ram disk



I think your right. Did you try doing "sudo -u $user rsync blah blah blah"? You may want to change the mkdir command too.

---

### Post by LewisTM on 2012-08-27
You are running your script - and so rsync - as root; the superuser will end up owning the copied files. You have to add the -o option in addition to -p (copy **owner** and perms) or simpler, the -a option (equals -rlptgoD). 

Cheers!

---

