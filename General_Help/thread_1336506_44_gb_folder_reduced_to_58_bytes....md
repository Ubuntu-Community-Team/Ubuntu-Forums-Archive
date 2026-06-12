---
title: "44 gb folder reduced to 58 bytes..."
date: 2009-11-24
forum: General Help
---

### Post by Iacoi on 2009-11-24
Okay, so I'm preparing to update to Win7 Ultimate and decide to back up my files, dumping roughly 44 gb of music, several movies, school work (high school senior, the work is no big loss ;)) and quite a few assorted programs that would take a very long time to reproduce. All the files manage to copy over to my Ubuntu partition, where I arranged them into one large folder entitled "Iacoi Backup (11/24/2009)" and are then successfully 7zipped into one 40 gb compressed file. After installing Win7 Ultimate the files are still located in full on my Ubuntu partition, and are completely intact. After moving the files over to my Windows Partition I find that the files do not exist anywhere on the Window's file system. Ubuntu shows one file on the Windows Partition entitled "Iacoi Backup (11/24/2009)" but it is a text file, and only 58 bytes. A deep scan with Recuva on Windows was not able to recover any files. So... yeah. Totally screwed right now, and kinda hoping for a miracle. Any help is appreciated.[-o<
[B]
Basic Info:[/B]
_Laptop:_ HP G60-445DX
            320 gb
            2.2 Ghz Dual-Core AMD
            3 gb RAM
            Dual-Boot (Win7 RC [170 gb], Ubuntu 9.10 [140 gb])

_Steps Taken:_ Ran Foremost... pretty sure I ran it incorrectly.
                    Ran Recuva (Deep Scan)
                    Checked Win7 RC backup, but was made after files were moved.

_Current State:_ Just about ready to kill something... ](*,)

---

### Post by drs305 on 2009-11-24
Any chance it might still reside on your Ubuntu partition. This command will inspect all folders for a file greater than 30GB:
```

sudo find / -name '*' -size +30G

```

---

### Post by phillw on 2009-11-24
> **Iacoi said:**
> Okay, so I'm preparing to update to Win7 Ultimate and decide to back up my files, dumping roughly 44 gb of music, several movies, school work (high school senior, the work is no big loss ;)) and quite a few assorted programs that would take a very long time to reproduce. All the files manage to copy over to my Ubuntu partition, where I arranged them into one large folder entitled "Iacoi Backup (11/24/2009)" and are then successfully 7zipped into one 40 gb compressed file. After installing Win7 Ultimate the files are still located in full on my Ubuntu partition, and are completely intact. After moving the files over to my Windows Partition I find that the files do not exist anywhere on the Window's file system. Ubuntu shows one file on the Windows Partition entitled "Iacoi Backup (11/24/2009)" but it is a text file, and only 58 bytes. A deep scan with Recuva on Windows was not able to recover any files. So... yeah. Totally screwed right now, and kinda hoping for a miracle. Any help is appreciated.[-o<
[B]
Basic Info:[/B]
_Laptop:_ HP G60-445DX
            320 gb
            2.2 Ghz Dual-Core AMD
            3 gb RAM
            Dual-Boot (Win7 RC [170 gb], Ubuntu 9.10 [140 gb])

_Steps Taken:_ Ran Foremost... pretty sure I ran it incorrectly.
                    Ran Recuva (Deep Scan)
                    Checked Win7 RC backup, but was made after files were moved.

_Current State:_ Just about ready to kill something... ](*,)

Your backup is still sat on the ubuntu partition ? i.e. it's only that they didn't copy over to the win area ?

Phill.

---

### Post by Iacoi on 2009-11-24
@phillw
I wish... That would be a pretty easy fix.

Using the find command only found five files, all of which either returned the error 'No such file or directory' or 'Input/Output Error'

---

### Post by phillw on 2009-11-24
Hmmm  (expletive deleted) springs to mind. How did you move them from the ubuntu area to the Win area ?

Phill.

---

### Post by phillw on 2009-11-24
I can only give you a couple of suggestions to investigate ....

[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

and

[http://en.kioskea.net/forum/affich-80216-urgent-how-to-recover-my-deleted-files](http://en.kioskea.net/forum/affich-80216-urgent-how-to-recover-my-deleted-files)

That, and wish you all the best.

Phill.

---

### Post by Iacoi on 2009-11-24
logged in as root, point, click and drag.

---

### Post by Iacoi on 2009-11-24
Okay... Recuva found my files after a deep scan... all 187669 of them... anybody want to explain to me WTF a .rim.gpu file is? Cause I found around 30000 of them....

EDIT: 247786 files.

---

### Post by Iacoi on 2009-11-24
Okay. Finally figured it out. Using HDGraph, I located a folder "C:\found.000" that contained a surprising amount of data for a folder that did not exist on my hard drive (ergo, it literally did not appear, but could be accessed through the command prompt). Upon further search my folder was located, in its entirety :D, within another subdirectory C:\found.000\dir0000.chk\ where Ubuntu had dumped the files.

---

