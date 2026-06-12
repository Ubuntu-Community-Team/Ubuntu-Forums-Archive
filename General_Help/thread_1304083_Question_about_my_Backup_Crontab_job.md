---
title: "Question about my Backup Crontab job"
date: 2009-10-28
forum: General Help
---

### Post by magicmax0 on 2009-10-28
Im planning to backup my 2nd Media drive onto my main OS drive. To make it convenient i decided to try crontab. So far i've used this line to great success:

"00 03 * * 1 tar -cjf /home/rigo/mediaBAK.tar.bz2 /media/mymedia"

So it runs at 3AM every Monday. Since im not short on space i've decided to modify it so it does not compress with bz2:

"00 03 * * 1 tar -cf /home/rigo/mediaBAK.tar /media/mymedia/"

I noticed when using that command it says:

"Removing leading `/' from member names"

What exactly does that mean? If i "extract here" on the tar file in Nautilus, will it overwrite my current "/media/mymedia/" directory? Where will it extract the contents of "/media/mymedia"? Ideally i would want it to extract into its own "mymedia" directory in "/home/rigo/" not in "/media/".

---

