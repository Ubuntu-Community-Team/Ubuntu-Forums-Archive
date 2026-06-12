---
title: "Partition - Need some help please :)"
date: 2009-10-26
forum: General Help
---

### Post by MariusEriksen on 2009-10-26
Hi. I recently installed Kubuntu 9.04 on a 5year old laptop. 

I decided to make two partitions on my hard drive. This resaulted in a problem: 

1st Partition: Primary, formated as ext4 with / as mount point: hda1
2nd Partition: Logical, formated as ext3 with /usr as mount point: hda4

I set the mount point to /usr, thinking this was just a name and some settings. Tho this resulted with all the other root files on the / hd. 
Did didnt happend.. Now my /usr folder is inside the 2. partition, due to moint point set at /usr. 

This was not my intensions at all :( Now I want to format the 2. partition again, as a logical drive wich are empty. If I format it now I guess I'll loose the entire /usr folder, causing the system to stop working? Can I just do a '$cp /hda4/usr /hda1/root/ without any further configuration? (Not sure about how to cp from one hd to another?)

And what should I set the mount point to? I want it to automaticly mount, without any important files inside. 
Thank you very much for your time:)

---

### Post by undecim on 2009-10-26
For what reason do you have those two partitions? And why the slow ext3 on /usr, where read time mot affects performance?

Were you looking to put /home (files and settings for computer users) on a separate partion? (which I strongly advise; it makes updates much easier)

If you don't have any files you will miss on the hard drive, it's probably best to just reinstall.

---

### Post by MariusEriksen on 2009-10-26
Im going to store some games and other stuff on it. 
I used ext3 becaus I read somewhere that ext4 (if thats whats in ur mind?) was somehow still unstable. Is this true?

Hmmm, about the /home partition, do I just set the mount point to /home? And.. Is this possible at this state? 

Got damned it.. Reinstall again? Gues so.. 
What size should my / partition be? Only got a 60gb hd, so would like the /home partition to be biggest possible. Regards.

---

### Post by MariusEriksen on 2009-10-26
is ext4 the right way to go on all my partitions? Whats the difference on this and ext3?

---

