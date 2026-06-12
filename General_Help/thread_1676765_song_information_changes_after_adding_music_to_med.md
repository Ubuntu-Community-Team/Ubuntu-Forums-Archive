---
title: "song information changes after adding music to media players"
date: 2011-01-27
forum: General Help
---

### Post by kolo-01 on 2011-01-27
this is probably going to seem like quite an odd post, and something that most of you probably won't even be aware of, but it is something that affects me a lot, maybe cos im slightly ocd about how things are organised on my computer, but here goes:

when adding music to a music player, say banshee- which is my favourite ubuntu one, many of the tracks information are often 'auto corrected', im not sure how this is done, whether there is information stored on the file, or whether the player accesses a database on the internet, but basically this is not what i want, i want to be able to upload the files and change them from the state that they are when i upload them. can anyone else relate to this problem? or know of a solution..

the thing is, it is only about 20% of the files that are changed after uploading and i have no idea what the reason is for it, and its not restricted to banshee, it happens with just about all media players

---

### Post by AlphaLexman on 2011-01-27
You could just change the permissions of the *.mp3's so that programs can not update | change them. (-r--r--r--.) or:
```
chmod 444 *.mp3
``` will make them read-only.

---

