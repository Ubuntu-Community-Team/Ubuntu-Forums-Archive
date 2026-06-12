---
title: "Back it time backup utility issues"
date: 2010-01-06
forum: General Help
---

### Post by ashakeandfrys on 2010-01-06
How many of you guys use Back In Time as your backup utility? I tried using it, and it doesn't copy all of the folder contents to the backup drive in one pass. For example, it will copy 26 out of 80-ish gigs of data. To further complete the backup, I have to hit the "Take a snapshot" button to do another pass to add more data to the snapshots. I have to do this a couple times to get all the data.

Does anyone else have this issue?

[UPDATE] It appears to copy all of the files at once, so long as you only select one backup location at a time. I was backing up an entire multimedia drive, my home directory, and my usb drive. When I had it set to only do the multimedia drive, it copied all of the files, whereas it wouldn't if I had set it up to back up all 3 locations at the same time. I guess the lesson here is to backup one location, then add another, get another snapshot, and repeat.

---

### Post by ashakeandfrys on 2010-01-07
Problem solved. My backup drive came formatted with FAT32, which has a file size limit of 4 GB. This fact completely slipped my mind! Since, I have formatted with NTFS, in the interest of interoperability.

Back In Time works perfectly.

---

### Post by Jeanfrancoissven on 2010-01-08
Thanks, I didn't understand why it suddenly stopped working. My vdi of win xp on virtual box was about 8 gig, so I excluded that file in the preferences...

---

