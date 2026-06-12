---
title: "Bacula Help!"
date: 2010-04-14
forum: General Help
---

### Post by truKrewl on 2010-04-14
Hello all

I have an ubuntu (8.04.3) server where I use bacula to make backups of the files stored on the server. Ive been trying to find a solution (with no luck) trying to succesfully implement the following:-

A Backup tape for each day of the week besides Thurs which is resused on a weekly basis.

For the thursday tapes we have a backup tape corresponding to the week number that the thursday falls so for the first thursday of the month it would be ThursOne For example. These tapes are resued on a monthly basis. We then have a monthly tape that is used on the last thursday of the month. These tapes will be resused on a yearly basis.

Another requirement is just in case a tape is accidently not changed a backup should still occur regardless of what tape is in the drive (so if its tuesday and mondays tape is still in the tape drive it should rewrite that tape).

I did have this successfully set up where the tape was appended after each use rather than being recycled after the nightly backup. But then after a few weeks I would have to manually purge tapes when they became full (which isnt ideal - as Im not always in the office so in my absence it may be that a backup may not take place), so have been playing around and have now got the tapes to be marked as used after a max of 2 jobs (so the backup of the files and the catalog of the night). I also added this line 'Recycle Current Volume = yes' so that it would hopefully recycle the volume in the drive.

However what I am finding is that the tape that should be recycled is not, but in yesterday case the Mondays tape was recycled rather than the Tuesday although Mondays was the last written so Im not even sure why it choose to recycle this tape...

Any ideas as to how I would implement the above with the requirements...

Many thanks for any helpful responses in advance!

t.

---

### Post by truKrewl on 2010-04-14
Hmm was just thinking...maybe if a script is executed before the job is run which would purge the current volume and recycle it and by setting the retention periods for the other tapes to something ridiculously high would ensure that the current tape in the drive is used for the backup.

Would this work??? And any ideas how I would write such a script???

Thanks again for any help! :)

---

