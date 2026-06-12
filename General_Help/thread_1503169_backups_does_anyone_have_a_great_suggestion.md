---
title: "backups: does anyone have a great suggestion?"
date: 2010-06-06
forum: General Help
---

### Post by Sandertje on 2010-06-06
Hi,

Recently, i've had a hard drive failure. Since I'm not the most organized person running around this planet, i didnt do backups much (yes, I know it's my own fault :P). So I lost quite a lot of data. I don't want that happening again, so I bought a new external Hard Disk (I can't really afford a RAID-array). Now, I could backup manually, but I wondered if there's any good software that can do it all for me. I've made a list of requirements:

1) Must backup data automatically
2) Detects (un)plugging of external media
3) No use for multiple copies of files on one disk
4) No money to do RAID; must be software-augmented
5) Preferably transfers only new and modified files (transferring unmodified files would be redundant)
6) Option to include and exclude certain folders (my main issue's about multimedia files and documents. I'm not very concerned about system files (since I can install ubuntu again anyway)). 
7) Option to set my new external HDD as the default backup medium


Does anyone have a suggestion? 
Thanks in advance!! :D

---

### Post by sdennie on 2010-06-06
It depends on if your primary concern is disk failure or user failure.  If it's disk failure, then RAID and external backups are the only way to go.  If it's user failure then something like rsnapshot might solve your problems.  Even in the case of user failure, you probably still want to have some sort of external backup.  

You only lose a lot of important data once...

---

### Post by BobvanderPoel on 2010-06-06
I used to want to do things the hard way ... and never really had much success :) 

I suggest you install Back In Time (it's right in the lucid repository). About the only thing you _need_ to do is to set a backup device ... it does the rest by itself. No problems, really.

---

### Post by Sandertje on 2010-06-06
I've just installed "Back in Time". It nicely does everything in my requirements lists. It's now backing up my old external HDD to the new external HDD, guess it might take some time :P.

---

