---
title: "no luck with cron"
date: 2010-01-15
forum: General Help
---

### Post by sn0m on 2010-01-15
chaps why dosen't my script run in cron

#!/bin/sh
#script to rsync my pendrive
DIRECT=/media/MemoryCard
if [ -d "$DIRECT" ]; then
  /usr/bin/rsync -qrtu /media/MemoryCard/MedicalNotes/ /home/koli/MedicalNotes/ 
  sleep 5s &&
  /usr/bin/rsync -qrtu /home/koli/MedicalNotes/ /media/MemoryCard/MedicalNotes/ 
  sleep 5s &&
  /usr/bin/rsync -qrltDh --delete --prune-empty-dirs --size-only --ignore-errors /home/koli/Music/mp3_radio_files/ /media/MemoryCard/mp3_radio_files/
else
  exit
fi

Any help appreciated
Sokol

---

