---
title: "Why no 'Missing Files' in Rhythmbox"
date: 2010-05-23
forum: General Help
---

### Post by jamesisin on 2010-05-23
I had a drive failure on my media server.  I have replaced the drive and since my backup was a bit out of date I lost some material.

I thought, no biggie, I'll get everything back in order and just use the Missing Files list in Rhythmbox to figure what's missing.

Problem.  Though the file count diminishes as Rhythmbox scans the library for file changes, nothing is being added to the Missing Files list.  I have done this on two machines (one the server itself, the other across a Samba share).  Same behaviour.

I have never seen Rb count down files and not add them to the Missing Files list.

What's going on here?

---

### Post by jamesisin on 2010-05-24
Anybody?

---

### Post by jamesisin on 2010-05-25
I have created a couple of posts on two other Rb forums I found:

[http://www.last.fm/group/Rhythmbox/forum/8096/_/625786](http://www.last.fm/group/Rhythmbox/forum/8096/_/625786)

[http://www.forumjar.com/forums/topic/Why_no_'Missing_Files'_in_Rhythmbox%3F](http://www.forumjar.com/forums/topic/Why_no_'Missing_Files'_in_Rhythmbox%3F)

Would love some attention on this one...

---

### Post by jamesisin on 2010-06-02
I have subsequently moved/removed folders (duplicates from the backup) and those folders DO appear in a Missing Files list.  Not sure why the one time I needed a Missing Files list I got nothing.

---

### Post by AAK on 2011-06-22
I am having the same issue. I also tried deleting an existing song and *that* wound up showing up in "Missing Files," but not the tracks I needed. Have you resolved this issue?

---

### Post by life in color on 2011-06-23
I believe I had a similar issue though it fixed itself I think. Is there anyway you could reconnect the old drive to Rhythmbox? That may bring back the missing files 'tabs'. I would check any Rhythmbox directories, your music folder, etc. I'm clueless for this one, I'm just telling you what I would try to do.

---

### Post by AAK on 2011-06-23
I wound up using xmlstarlet on ~/.local/share/rhythmbox/rhythmboxdb.xml to derive a list of my missing tracks, but, after reading your post, I think I could have just mounted *anything* at the same mountpoint indicated in the xml entries of my missing tracks and had them show up in the Missing Files section of Rhythmbox.

---

