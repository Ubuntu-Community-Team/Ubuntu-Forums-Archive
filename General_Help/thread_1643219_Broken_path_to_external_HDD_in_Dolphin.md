---
title: "Broken path to external HDD in Dolphin"
date: 2010-12-11
forum: General Help
---

### Post by AirWreck on 2010-12-11
I did a backup to an external drive without mounting it so it crammed my root partition to the brim.  No worries, some kind soul on here helped me out of that pickle by pointing me to where that partial backup ended up.  

However Dolphin now mounts my external as "John Doe 500gb -1."  "John Doe 500gb" still exists in Dolphin and I cannot find a way to blow it out so my backup paths are inaccurate as they are not looking for the "-1."  Consequently Luckybackup just dumps the backup right back into the root again.

To resuscitate my root partition, I was able to delete files from inside the "JD 500gb" but I cannot delete directories or the whole thing altogether.  I tried going into system settings and "forget" it as a drive but that was not the right animal for the job as it doesn't clear Dolphin.  I guess I could just rename the drive and make new backup paths but I'd like to learn how to fix the problem instead of a workaround.  I did search the net and this forum because I figured it was a common question but couldn't find the right search parameters to get an answer.

Thanks.

---

### Post by AirWreck on 2010-12-19
bump...

---

### Post by tredegar on 2010-12-19
Remove all external drives
Open a terminal
```
# become root
sudo -i
# change to the /media directory
cd /media
# remove (by force) these two directories and all their contents
rm   -rf   "John Doe 500gb-1"   "John Doe 500gb"
# finish up
exit
exit
```
Replug the drive

---

