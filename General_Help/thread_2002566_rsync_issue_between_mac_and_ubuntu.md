---
title: "rsync issue between mac and ubuntu"
date: 2012-06-12
forum: General Help
---

### Post by rectifiercc on 2012-06-12
Question here for the rsync pros:

I'm backing up some directories with old sound designer 2 files from a mac to my ubuntu 9.10 server. It seems to corrupt the files to an unrecognizable format. I've tried using -X to preserve extended attributes like resource forks and it doesn't help. I get this error on every file:

rsync: rsync_xal_set: lsetxattr(".Snr white noise.L.hAAny7","user.com.apple.ResourceFork") failed: Operation not supported (95)

Is this due to the drive being formatted as ext4?

the mac has rsync 3.0.9
the ubuntu box has rsync 3.0.6

thx

---

### Post by rectifiercc on 2012-06-12
One more bit of info is that I can copy the files successfully if I drag and drop from the Finder to the ubuntu drive in my LAN. So ext4 formatting is obviously not a problem. There must be a way to do it with rsync. Anyone? :-)

---

