---
title: "Recover overwritten files from ext4 + encrypted encfs home directory"
date: 2011-10-09
forum: General Help
---

### Post by medicdave on 2011-10-09
Made a pretty major oops - when pulling in photos from my digital camera, I used `mv` and accidentally overwrote a sizeable quantity of images from a family vacation; my camera resets image file numbering each time the card is inserted. **This was stupid, and I should have known better.** Any resulting beratement will be well-deserved! :)

My home dir is encrypted using Ubuntu's standard installation-time facility (encryptfs?). I've built and used the `extundelete` utility to scrub the partition (/dev/sda4, a dedicated /home partition) and recover some data. The recovered files look as follows:

```
drwxr-xr-x  3 root root   4096 2011-10-08 20:53 .ecryptfs
-rw-r--r--  1 root root  20480 2011-10-08 20:53 file.4993458
-rw-r--r--  1 root root 282624 2011-10-08 20:53 file.4994331
-rw-r--r--  1 root root  12288 2011-10-08 20:53 file.4994332
-rw-r--r--  1 root root  12288 2011-10-08 20:53 file.5118148
```

Inside .encryptfs is my homedir, containing .Private, containing several levels of encrypted directories and files. 

If I can manage to find the encryption keys written down during the initial Ubuntu installation process, will it be possible for me to decrypt the recovered tree?

Alternately, could I merge (possibly using Meld?) the recovered encrypted dirs and files into [a copy of] my live encrypted home directory then decrypt the files by logging in normally?

Any help will be much appreciated!
Thanks,
medicDave

---

### Post by medicdave on 2011-10-09
Managed to decrypt my recovered files using the instructions in this post:

[http://gimi.name/snippets/undelete-ecryptfs-encrypted-files/](http://gimi.name/snippets/undelete-ecryptfs-encrypted-files/)

However, images weren't there... :( Now trying to recover anything remaining on the memory card using PhotoRec...

---

