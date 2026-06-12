---
title: "copying contents of /home failed"
date: 2011-02-07
forum: General Help
---

### Post by comp3820 on 2011-02-07
I tried to use cp -r from root to copy the contents of /home to a different partition, but nothing got moved.

Here is my situation: I am maintaining a "public" (family) computer. On this computer I have a separate partition called "Family" that is a samba share for everyone on the network. Also on this computer I have the default /home directory.

Ideally, all files should be saved on the "family" share. The problem is that the home directory is called "family" (because the user is "family") and the share is also "family." That's a little too confusing for everyone.

So I'd like to copy everything to the share, and set that as the new home directory, so that all files by default are saved on the share, and can be accessed by everyone on our network.

What happened is that I first tried to set up the share as the home directory by following an ibm tutorial ([http://www.ibm.com/developerworks/linux/library/l-partplan.html](http://www.ibm.com/developerworks/linux/library/l-partplan.html)). Just after pressing enter on "cp -ax", I realized that the -ax might mean I was going to lose all the files in the current destination. The file transfer process took forever (keeping me biting my nails to see if I had really lost everything in the drive), but in the end the screen went blank, and the HD light stopped blinking, so I restarted, and everything was there. Completely unchanged, and not copied, either.

So I went back and copied it with cp -r. Same thing. Took a few minutes, but when all was said and done, nothing was changed.

So I guess I'm looking for advice on how to merge my two directories and make them both /home and a share, since whatever I am doing is obviously not working.

TIA
comp3820

---

### Post by blueridgedog on 2011-02-07
I recommend rsync.

> sudo rsync -av /home /path/to/family --log file=/path/to/where/you/want/log/$(date +%Y%m%d)_rsync.log

---

### Post by Old *ix Geek on 2011-02-07
Try adding some flags to **cp**:

```
cp -pRv /OLD_DIRECTORY /NEW_DIRECTORY
```

This will preserve [-p] each file's attributes (owner, etc.) as it recursively [-R] copies files, showing you [-v] what it's doing as it's doing it. If it fails, you should see why!

---

### Post by blueridgedog on 2011-02-08
If you try the cp command, don't forget to use sudo.

---

### Post by Old *ix Geek on 2011-02-09
> **blueridgedog said:**
> If you try the cp command, don't forget to use sudo.Unnecessary as s/he is running this as root, as stated in their OP.

---

