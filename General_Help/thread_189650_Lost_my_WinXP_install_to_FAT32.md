---
title: "Lost my WinXP install to FAT32"
date: 2006-06-05
forum: General Help
---

### Post by moogatu on 2006-06-05
I've installed Ubuntu successfullly; however, it seems that I also managed to format my WinXP partition as FAT32. Obviously (or perhaps not obviously), I want that data back. The partition was originally NTFS, now it's a blank FAT32.

I need a data recovery tool, I think, so I'm turning to the experts here for advice.  I have not written to the FAT32 partition since it became FAT32, so I hope that makes things easier on my recovery.

Any recommendations? I know I should have backups, but... yeah, we all know how that shakes out sometimes. 

Can I be helped?

---

### Post by mscman on 2006-06-05
Hmm...  I've done data recovery in Windows in the past, but I haven't done any from Linux.  I'll have to take a look at some possible tools to see what can be done.  Hopefully your data wasn't completely overwritten. :???: If that happens you can't get it back...  I'll post back in a few minutes.

---

### Post by moogatu on 2006-06-05
[QUOTE=mscman]Hmm...  I've done data recovery in Windows in the past, but I haven't done any from Linux.  I'll have to take a look at some possible tools to see what can be done.  Hopefully your data wasn't completely overwritten. :???: If that happens you can't get it back...  I'll post back in a few minutes.[/QUOTE]

I asked about Linux tools because, well, my Ubuntu install works flawlessly. Plus, it'll teach me a little more about the "guts" of Linux.  

Thank you for looking into some options for me.  :D

---

### Post by mscman on 2006-06-05
Well, after a quick look I found a program that *MAY* suit your needs.  It's called [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), it runs on multiple platforms and can recover almost any file system.  I'm not sure how it works or how well it works, but it seems to be worth a shot.  Good luck!  Data recovery isn't fun...

---

### Post by moogatu on 2006-06-05
WOOT, thank you. I'll certainly look into it and post my results. :)

---

### Post by moogatu on 2006-06-05
Okay, I'm lost. I need to ./configure this thing, but I keep getting "command not found," even though I'm in the directory the docs tell me I need to be in.  Am I missing something obvious?

Yes, I'm a Linux n00b. Please bear with me, I *want* to learn.

---

### Post by jocko on 2006-06-05
I can think of two reasons for that error. Either the file is not in that directory, or it's not executable. Check that there is a file named 'configure'. If there is, try running this command first:
```
sudo chmod 755 configure
```

Hope I could help. Good luck!

---

### Post by moogatu on 2006-06-05
My error here; I did "sudo testdisk_stable" when I should have done "sudo ./testdisk_stable" - it's running now...

---

### Post by moogatu on 2006-06-05
FYI, it's not really going to help. Going from a NTFS format to FAT32 is, it seems, pretty much unrecoverable.  So, I lose data and get a fresh WinXP install.

At least it's my work computer, and not my home one. Time for backups at home, I think! lol.

---

