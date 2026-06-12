---
title: "data lost"
date: 2012-02-27
forum: General Help
---

### Post by 001neeraj on 2012-02-27
I am using Ubuntu 11.04. I just execute the command  ```
sudo rm -rf *
```  from terminal after a few minutes i there  is nothing left inside my ubuntu partition. Then i reboot my system. There appears grub rescue prompt. What should i do to access my lost data in Ubuntu???

---

### Post by philinux on 2012-02-27
> **001neeraj said:**
> I am using Ubuntu 11.04. I just execute the command  ```
sudo rm -rf *
```  from terminal after a few minutes i there  is nothing left inside my ubuntu partition. Then i reboot my system. There appears grub rescue prompt. What should i do to access my lost data in Ubuntu???

Why you did that without checking firsts beats me. 

Anyway the only thing you can try is photorec which is part of the testdisk package. You need to run a livecd install testdisk and use photorec. But you need to read up on photorec first.

---

### Post by miasmablk on 2012-02-27
+1 for photorec just make sure you specify the files you wish to recover like .mp3, .jpg, etc or you end up with tons of directories full of stuff you don't wan't and you'll never be able to find anything, also avoid writing anything to the affected hard drive to avoid overwriting lost data and next time BACK UP :popcorn: good luck man

---

### Post by QIII on 2012-02-27
I would also recommend photorec.  I've used it many times before to rescue people.  It doesn't do so well at recovering people's iPod music files on Windows because the Apple software obfuscates the file names and the database the software uses to find the files in the right albums and the right order is proprietary and inscrutable.  You can recover the files, you just won't be able to make heads or tails of them.

Just so you know: if someone suggested that command, you were the victim of an "rm troll".  A cruel prankster.  The command basically says "forcibly delete everything recursively".

rm      "remove", or delete

-r        recursive

f         force

*        everything (although the trolls usually say "/".  I didn't know it would work quite like the way you did it.)

I rarely use the rm command off hand.  I generally use mv (move) to a "_bak" so I can be sure I haven't messed something up -- we all make typos.  If things still work, I'll use rm on that _bak file - specifying the full path and file name.

Next time ask before using rm or a wildcard.  There are small people who make themselves feel big by screwing the unsuspecting.

---

### Post by 001neeraj on 2012-03-04
Thank you all...for replying me...i installed 11.10 in my computer...

---

### Post by raja.genupula on 2012-03-04
you did that even you know its consequences ?

have you seen this 
[http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54)

---

