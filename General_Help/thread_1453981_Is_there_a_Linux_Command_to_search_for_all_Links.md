---
title: "Is there a Linux Command to search for all Links?"
date: 2010-04-14
forum: General Help
---

### Post by held7over on 2010-04-14
Ubuntu 9.10 Gnome

Something is acting as though there is a link in my /home/user file structure which is adding almost 40 gig to my backup! I can't find it with the diff command, as it says everything is common....meaning, I think, everything matches up. Yet my system monitor sees my primary drive as being 85% full and my backup (the same size drive) being 99+% filled!

Is there a linux command that would search through my file structure and list all the locations of any links?

And is a "link" the only thing that would create a situation like this?

Thanks  :)

P.S. That I know of, I didn't create any links. Whatever it was, seems to have started yesterday.

---

### Post by john newbuntu on 2010-04-14
Start off with a command like this from your home directory:

```
du -k | sort -n
```Start from the last line and work your way upwards to see the culprit file/directory.  Clear your browser cache and see if it helps.

---

### Post by held7over on 2010-04-15
Thanks for the input john newbuntu!

My browsers all automatically clear cache on shutdown. 

However, your du command, which I eventually evolved into "du --max-depth=1 -h" greatly helped me discover the problem. It is not a link problem at all, instead, it is a reserved space problem. 

I use ktorrent and often just have things loaded up in it that I want to download....someday, but am not downloading now. There is an option in ktorrent that allows you to enable Reserving Space for the size each torrent is going to require on your drive. However, on my system, this is NOT ENABLED because I want no reserved space, and thus, on my primary drive, no additional space is being reserved, BUT FOR SOME REASON when a backup is being made, the space ending up RESERVED on the backup! This seems a bit strange, though, because if nothing is reserved on the primary drive, how would the rsync backup or just a straight copy command know to reserve space? 

I have submitted that question to ktorrent concerning this. This must be what is happening, as the compared numbers coming from the du command don't lie. If I get a solution, I will post it here. Or, if anyone else has one, feel free to suggest it! Thanks.

---

