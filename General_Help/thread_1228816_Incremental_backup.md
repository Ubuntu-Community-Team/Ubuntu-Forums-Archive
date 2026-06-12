---
title: "Incremental backup"
date: 2009-08-01
forum: General Help
---

### Post by swaprava on 2009-08-01
I want to take backup of the data in my laptop to a remote PC with sufficient memory space. The data I have is of huge size, and backed up once. Now, the next time I want to take a backup, the new data has very little changes with the one already backed up. I don't know how only the difference in the two data can be backed up. Can you please advise? Usually I tar-ed and gunzipped the initial data. I had come across a few threads on rsync, but don't know how it works. If the incremental backup is possible, it will save a lot of copying time. I tried googling, not much luck, if you have come across a good tutorial on this, please share me the link.

thanks in advance ...

---

### Post by rtrdom on 2009-08-01
If you will be doing this sort of thing regularly, may I suggest UNISON.
I use it to keep several computers "in-sync" and it does an excellent job.
One must set up profiles for each computer/file. However I have one profile that synchronizes the entire /home/name to the second computer's /home/name. It can also be used with ssh (which I use remotely) to keep the
computers in sync.  Hope this helps.

---

