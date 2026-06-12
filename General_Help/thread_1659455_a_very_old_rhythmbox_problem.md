---
title: "a very old rhythmbox problem"
date: 2011-01-04
forum: General Help
---

### Post by flipper T on 2011-01-04
a post from this forum from 2006 !

"I recently tried to add two new podcast feeds to my Rhythmbox (0.9.6; I'm running Dapper), and they both failed to download. What's worse, the failed downloads caused Rhythmbox to crash.

I don't care too much about these particular podcasts; I can live without them. But I don't want my music player crashing on me every time one of these bad podcasts updates. So i'd like to remove the feeds entirely.

Unfortunately, I can't find any way to do that. If I just delete the podcasts themselves, they are just added again the next time the player updates. And there's no menu or dialog option to "Delete Podcast Feed".

Presumably these feed URLs are stored in a configuration file somewhere. Can anyone tell me where to look?"

i now have this same problem. only difference being that there is now an option to delete feed. i try this on the bad feed and the app crashes !

anyone located tonfig file yet ?

---

### Post by howefield on 2011-01-09
Try renaming the Rhythmbox folder in ~/.local/share.

Rhythmbox should create a new rhythmdb.xml file. If it works, you may delete the original folder.

---

