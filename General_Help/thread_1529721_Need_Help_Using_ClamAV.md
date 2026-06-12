---
title: "Need Help Using ClamAV"
date: 2010-07-12
forum: General Help
---

### Post by gjrepicky on 2010-07-12
I'm trying to run clamav in a terminal with the command:

       clamscan -r /

to scan the entire filesystem.  I get a rapid, fairly long, sequence of messages, the last few of which are:

 /sys/devices/virtual/block/ram0/capability: OK
LibClamAV Warning: fmap_readpage: pread fail: asked for 3997 bytes @ offset 99, got 0
/sys/devices/virtual/block/ram0/stat: OK
LibClamAV Warning: fmap_readpage: pread fail: asked for 4078 bytes @ offset 18, got 0
/sys/devices/virtual/block/ram0/inflight: OK
LibClamAV Warning: fmap_readpage: pread fail: asked for 4095 bytes @ offset 1, got 0
/sys/devices/virtual/block/ram0/power/wakeup: OK
LibClamAV Error: cli_readn: read error: No such device or address
/sys/devices/virtual/block/ram0/trace/enable: OK


and then nothing but a flashing cursor for as long as I'm willing to let the program continue.  If it matters, I'm running Lucid on an Asus Eee netbook (highly recommended, incidently!).  Any idea what I'm doing wrong?

Thanks, 
George

---

### Post by bobcollard on 2010-07-12
> **gjrepicky said:**
> I'm trying to run clamav in a terminal with the command:

       clamscan -r /

to scan the entire filesystem.  I get a rapid, fairly long, sequence of messages, the last few of which are:

 /sys/devices/virtual/block/ram0/capability: OK
LibClamAV Warning: fmap_readpage: pread fail: asked for 3997 bytes @ offset 99, got 0
/sys/devices/virtual/block/ram0/stat: OK
LibClamAV Warning: fmap_readpage: pread fail: asked for 4078 bytes @ offset 18, got 0
/sys/devices/virtual/block/ram0/inflight: OK
LibClamAV Warning: fmap_readpage: pread fail: asked for 4095 bytes @ offset 1, got 0
/sys/devices/virtual/block/ram0/power/wakeup: OK
LibClamAV Error: cli_readn: read error: No such device or address
/sys/devices/virtual/block/ram0/trace/enable: OK


and then nothing but a flashing cursor for as long as I'm willing to let the program continue.  If it matters, I'm running Lucid on an Asus Eee netbook (highly recommended, incidently!).  Any idea what I'm doing wrong?

Thanks, 
George
I'm not sure how long you are willing to wait, between 2.5 and 4GB takes a long time.  For a good graphical user interface try klamav, I know it's made for KDE but you can see what's going on.

---

### Post by gjrepicky on 2010-07-14
Thanks; but I think there's something more going on here.  I let it run for about 4 - 5 hours, and got about 2 more lines of "error" messages.  Anybody have any other ideas?

TIA,
George

---

### Post by WorMzy on 2010-07-14
clamtk is the GTK equivalent of klamav, just in case you were wondering.

I'm not familiar with this error, but try running your command as root, with sudo, rather than your regular user.

---

### Post by WorMzy on 2010-07-14
Actually, ignore the second part of my last message, I get the errors when I scan my /sys folder too. So try the following instead:
```
clamscan -r --exclude-dir=^/sys /
```

---

### Post by Cocytuss on 2010-08-11
You need to exclude sys dev and proc. the -i just shows infections. -r will go though the whole disk. Even though it is not a recommended I use pua (Possibly Unwanted Applications). I almost never get a false positive with it. scan-mail is a default but all the same I like to see it there. I put my my in my home dir. No files are deleted and I can deal with later.

~/sudo freshclam "updates your AV"

clamscan / -ir --exclude-dir=^/sys --exclude-dir=^/dev --exclude-dir=^/proc --detect-pua=yes --scan-mail=yes --log=/home/erik/clamscan.log 

All the best

---

