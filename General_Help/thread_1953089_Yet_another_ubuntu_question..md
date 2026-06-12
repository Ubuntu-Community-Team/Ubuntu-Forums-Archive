---
title: "Yet another ubuntu question."
date: 2012-04-05
forum: General Help
---

### Post by manji_kun on 2012-04-05
Recently, i got my desktop back online, and have been trying to upgrade to 11.10, but my software is no longer supported by any suppository, so i downloaded the .iso image onto a disc, and it's giving me some kind of error, saying "missing file" or something similar, how can i update to the latest stable version?

---

### Post by QIII on 2012-04-05
I've never liked getting my software from a suppository.  ;)

I think you mean repository.

Lucid's repositories should still be available.  Or are you using a different version than you have in your info?

We really need a better description of the error.  Could you jot down a more complete description?

Also, could you do

```
sudo apt-get update && sudo apt-get upgrade
```

in the terminal, then cut and paste any errors between code tags?

Lucid is stable.  11.10 is, too, but with 12.04 right around the corner it might be worth waiting a month.

---

### Post by manji_kun on 2012-04-05
yeah, i put in a new master hard drive and i used my old 9.04 disc for this desktop. 
 The error is 

"ISOLINUX 4.04 20110518 ETCD Copyright (C) H. Peter Anvin et al 
EDD: Error 0100 reading sector 35
ERROR: No configuration file found No DEFAULT or UI configuration found! 
BOOT:"

when i try to boot from the 11.10 disc i just made.

---

### Post by QIII on 2012-04-05
My initial impression, and probably the easiest to check, is that your image download was imperfect or the image burn was.

Did you check the md5sum after downloading?  Did you burn the disk on a low speed setting?

---

### Post by manji_kun on 2012-04-05
Right now I'm downloading 10.04 and going to burn that, I'm not sure how to change the burn speed though.

---

### Post by manji_kun on 2012-04-05
Ok, so i re burned to another disc at 8x speed, same issue, perhaps the download is bad?

---

### Post by wildmanne39 on 2012-04-05
Hi, you should burn the iso image for ubuntu at the slowest speed possible.

As QIII stated did you check the md5sum to make sure the download is good?
Thanks

---

### Post by wildmanne39 on 2012-04-05
Hi, I did some research on the issue and you should download ubuntu again using the torrent because it checks the file for corruption as it downloads and you may need to use another cd burner as well.
Thanks

---

### Post by manji_kun on 2012-04-05
haha, that's what i did, i just downloaded one of the alternatives from bittorrent, I'm going to use that one instead, but as for checking the md5sum, I'm not so sure how to do that ^_^;;

---

### Post by plucky on 2012-04-06
> **manji_kun said:**
> haha, that's what i did, i just downloaded one of the alternatives from bittorrent, I'm going to use that one instead, but as for checking the md5sum, I'm not so sure how to do that ^_^;;

[How To MD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I have found that torrents are pretty good when downloading, getting the .iso image correctly as it checks the files as it goes along.

Good Luck

---

### Post by mastablasta on 2012-04-06
if you feel up to it and with fast enough connection you can also try to upgrade end of life release to 10.01: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

