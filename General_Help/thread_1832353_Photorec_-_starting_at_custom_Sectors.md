---
title: "Photorec - starting at custom Sectors"
date: 2011-08-24
forum: General Help
---

### Post by ScubaSam on 2011-08-24
Hello all,

I'm currently in the process of trying to recover files from my hard drive, which went scrambled thanks to a lovely bug in Acer's Laptop software (if you've ever heard of Acer Arcade Instant On you may know what I'm on about). I'm booting off an Ubuntu CD at the minute and using photorec to try and get as much as I can off the old drive before I swallow the bitter pill of windows reinstall.

Photorec successfully recovered one of my partitions (the largely undamaged data one) without much trouble, but on the much more damaged C: partition that held my windows installation, it hangs about 10% of the way through the drive, at roughly the same place. After a bit of searching I've found mention of photorec.ses and its apparent ability to specify which sector you want photorec to start at. This photorec.ses file appears in my /home/ubuntu directory when the terminal starts running photorec. However, attempts to open the file in a text editor just give my "could not open" errors from gedit, as it "has not been able to detect the character encoding".

Does anybody know how I might open this file? Does anybody out there have any experience with using the photorec.ses file to skip over bad sectors? Searches of both google and this forum have yielded little info, this is probably the most relevant thread I found:

[http://ubuntuforums.org/showthread.php?t=1096161](http://ubuntuforums.org/showthread.php?t=1096161)

Any advice would be much appreciated! Would like to point out that I'm a fairly competent computer user (an engineering student) but this Ubuntu CD is the first time I've used Linux, so please be generous with your descriptions if possible =)

---

### Post by ScubaSam on 2011-08-24
Bumpity Bump.

---

### Post by CryptKeeper777 on 2011-10-07
I'm having exactly the same problem. I've started PhotoRec now three times, and it always stops at roughly (maybe even exactly) the same spot. 

Any way I can tell PhotoRec to start just after that "deadly spot"?

---

### Post by sicklittlemonky on 2011-10-22
For future reference, PhotoRec 6.13(WIP - Work In Progress, currently) correctly resumes from a previously stopped scan at the appropriate sector. And you can hack the start sector.

The sector to restart at is near the beginning of the .ses file, so this is handy for hacking around bad sectors. It's also handy when a file scan goes bad and never ends. I've seen it trying to find the end of a .doc file at 1GB+ ... luckily now you can (S)top the scan, quit out and bump the start sector. I'll request a feature for this.

Cheers,
Nick.

---

### Post by CryptKeeper777 on 2011-10-23
I managed to start the recovery after the bad sector. I just deleted all photorec.ses files, started the recovery and aborted it after a short time. Then I opened the newly generated photorec.ses file, deleted all sector entries up to the bad sector and entered a number near the bad sector. When I restarted the photorec recovery, it asked me if I want to resume the recovery, and it started near the sector I entered in the photorec.ses file.

But it resumed a good deal before the entered number; I suppose at the beginning of the sector containing the number in the photorec.ses file. I had to do it several times though, increasing the number in the photorec.ses file because it was too low and the recovery was aborted by the bad sector. But when the number was high enough, the recovery wasn't aborted anymore and went through right to the end.

---

