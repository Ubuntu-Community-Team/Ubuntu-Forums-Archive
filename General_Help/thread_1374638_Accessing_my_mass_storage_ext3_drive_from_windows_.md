---
title: "Accessing my mass storage ext3 drive from windows 7 x64"
date: 2010-01-07
forum: General Help
---

### Post by Jive Turkey on 2010-01-07
The ext2 driver installed by Stephan Shrieber's IFS Drives program isn't quite compatible with Win7 yet.  You can get it installed and mount ext2 & ext3 partitions with it (provided you have the right inode size on the filesystem) but the mounts do not persist after rebooting like they do with (all) other windows versions.

In the FAQ on his site I was able to find out the shell command I needed to mount them.
```
mountvol X:\ \\?\Volume"{persistent-volume-name}"
```
where persistent-volume-name is discovered (while the partition is mounted via the GUI) by issuing the command:```
 mountvol X:\ /L
```
...with X being the drive letter.

For fear of a drive letter collision I set out to automate this but couldn't find where windows was doing the drive letter assignment.  

I settled for creating a file mountx.cmd with the above mountvol command in it and using windows task scheduler to run it with escalated privileges at startup.  It works, but I'm sure thaere is a better way, perhaps somewhere in the registry?  Any suggestions?

---

### Post by x33a on 2010-01-07
I have been using ext2fsd on xp, and it works well.

some people have tried it on win 7, and claimed that it works, though it is not stable yet. you could give it a try.

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

