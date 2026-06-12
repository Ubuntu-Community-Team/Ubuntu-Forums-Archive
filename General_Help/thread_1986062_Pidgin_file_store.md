---
title: "Pidgin file store"
date: 2012-05-24
forum: General Help
---

### Post by craigmcfly on 2012-05-24
Hi all,

I've just backed up my files, reformatted and installed 12.04 LTS 64BIT from the alternate CD.

As I usually do when I upgrade, I backed up the .purple folder, then slotted it back into place after the reformat and installed pidgin. However, pidgin is not reading from that folder - it's started a clean setup. Even if I close pidgin, rsync the files over again, and start back up, it just keeps reading the original config.

Has something changed in the way Ubuntu interacts with pidgin? 

Any help appreciated.

Cheers,

Craig

---

### Post by papibe on 2012-05-24
Hi craigmcfly.

Try running pidgin from the command line using the debug option:
```
pidgin --debug &> pidgin.txt
```
Wait until pidgin connects, and in another terminal:
```
more pidgin.txt
```
Usually the first lines reports access to ~/.purple

I hope that helps, and tell us how it goes.
Regards.

---

