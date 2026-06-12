---
title: "I can not use update in ubuntu 10.10!!"
date: 2011-03-02
forum: General Help
---

### Post by pavelexpertov on 2011-03-02
When i use update manager, i get an error message that looks like that ```
W:Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  
, W:Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2  
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```
what can i do about it?

---

### Post by ubudog on 2011-03-02
Hmm...

You may want to subscribe to this thread, because it appears some repos are down/slow now.

[http://ubuntuforums.org/showthread.php?t=1698397](http://ubuntuforums.org/showthread.php?t=1698397)

Also try this in a terminal:
```
sudo apt-get update
```

That may give you some more detailed errors, or maybe not.  It could be the same thing.

---

