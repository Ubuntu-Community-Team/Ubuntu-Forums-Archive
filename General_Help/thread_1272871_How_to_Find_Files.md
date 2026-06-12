---
title: "How to Find Files"
date: 2009-09-22
forum: General Help
---

### Post by mcedata on 2009-09-22
I've been using Ubuntu, Edubuntu at present, for a couple of years and am an old hand at DOS, so I'm not a complete novice at the command line. However, I'm a bit stumped with something.

I use Simple Backup. The backup files are descriptively named, as in
2009-8-23_17.58.06.555481.linux.ful.  For the last several weeks, when I do a full backup, the backup files most frequently do not get to the destination I designate in Simple Backup.  As a result, I seem to be spraying 5 or 6Gb files all over the hard drive...though occasionally, the backup file gets to the proper destination, so I do have usable full backups.

Problem is, I've sprayed so many of them around that my 80-GB hard drive is just 10Gb shy of being full.  Several weeks ago, I had about 50Gb free.

I've tried to find those files with the file browser and with Dolphin, but can't locate them. I've also tried to locate them from the command line, but no luck.(a bit of difference between DOS and Linux...!)

Can anyone give me some tips on how to locate those things so that I can delete them? Any help if very much appreciated!

Steve

---

### Post by JuergenF on 2009-09-22
Try in a terminal window
```
find / -name "*.linux.ful"
```If your backup script runs as root, prepend a 'sudo' - or may be anyway; who knows where they are ;)

But you should find out **why** they don't show up where you want. Any renaming of directories recently? 'Special' chars in the destination? etc.

---

### Post by credobyte on 2009-09-22
```
find / -size +1000000k
```

Will find all files, larger than 1Gb .. you can add -name parameter to make your search a little bit cleaner.

---

### Post by sisco311 on 2009-09-22
try:
```
find / -size +2G -name "*linux*" -exec ls -alh {} \;
```

EDIT: i'm slow. :)

---

### Post by mcedata on 2009-09-24
JuergenF, credobyte, and Sisco311, thanks for the help. Haven't had the chance to try the commands yet (so much to do, so little time...), but I'm sure one or the other of them will work. I see the logic in them.

Thanks again,

Steve

---

### Post by mcedata on 2009-09-26
JuergenF, sisco311, and credobyte...thanks again for your help. Found those offending files and nuked 'em, now have my free 59GB back again. Also found out what was going wrong with the backups and got that fixed, so all is well. Salute!

Steve

---

### Post by sisco311 on 2009-09-26
> **mcedata said:**
> JuergenF, sisco311, and credobyte...thanks again for your help. Found those offending files and nuked 'em, now have my free 59GB back again. Also found out what was going wrong with the backups and got that fixed, so all is well. Salute!

Steve

Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

