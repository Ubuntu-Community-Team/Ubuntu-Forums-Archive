---
title: "ddrescue, dd_rescue, dd_rhelp"
date: 2010-02-28
forum: General Help
---

### Post by Maximalminimalist on 2010-02-28
Hello everyone!

My hard drive crashed and I try to recover it now. I let dd_rhelp running for a while and whenever I restart it, it begins from the same point. It says that it has a bad log format and is starting the 'slow mode'.
I would like to use ddrescue as the author of dd_rhelp suggest but with the package ddrescue I have no ddrescue command. (Only dd_rescue.)

I'm getting kind of confusing if it's the same or not after browsing around...

I feel like there is a big amount of data already rescued but not the whole partition. (around 750 GB) But my /home should be around 900 GB.

Most of the partition was empty, so maybe I already have almost everything.
I have to know if it's everything or not (or everything I can save) because I will erase the whole data on the hard disk and use it for jfsrec the .img file back on the hard disk.

I hope somebody can help me! :)

Thanks in advance. ;)

---

### Post by lavinog on 2010-02-28
dd_rescue is the program that is installed with the ddrescue package.  I think this was because there was another program called ddrescue at one point.

For future reference you can list the files that are part of a package:
```

dpkg --listfiles ddrescue

```

Did the drive crash or did the partition get corrupted?
If the drive crashed, I wouldn't try and put data back on it.
If the partition was corrupted, you should take a look at the testdisk package.

Find out why you lost the data...even if you are able to still use the drive, the problem could come back again soon.  (Check the SMART information for clues about sector relocation...etc) The drive should have a warranty, you might be better off sending it to the manufacturer for replacement.

---

### Post by Maximalminimalist on 2010-02-28
The partition got corrupted. I had arch linux on my desktop and there was a crash of X. New installation (of arch) also results in a crash of X. Ubuntu works fine. I haven't tested the hard disk yet because I want to save the data first.

(The drive is not mountable.)

---

### Post by lavinog on 2010-02-28
you don't need to mount the drive when using testdisk (and photorec)

---

