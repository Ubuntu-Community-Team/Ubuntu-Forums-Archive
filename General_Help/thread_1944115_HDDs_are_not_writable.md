---
title: "HDDs are not writable??"
date: 2012-03-20
forum: General Help
---

### Post by CProgramming on 2012-03-20
Hello,
I have 3 Hard disk device on my computer. (ScreenShoot #1 attached).

first : "320GB Hard disk",
second: "500GB Hard disk",
third : "1TB Hard disk".

They are not writable:

for example, when I try to move file from music folder:

Source: /home/nimrod/music/linkin park - in the end ,
destenation: /media/A4D8E02ED8E00082/

I'm getting the following error message:

--------------------------------------------------

Error while copying to "A4D8E02ED8E00082".
The destination is read-only.

--------------------------------------------------

A4D8E02ED8E00082 is the 1TB filesystem (as you can see at #1 screen shoot).

screenshot #2 attached.

Only "/home/nimrod/*" folders are writable.

that's problem start appear yesterday. All worked well before. 

how can I make these HDDs writable again?

p.s: When using ubuntu liveCD , the HDDs are writable.

Thanks!!

---

### Post by dcstar on 2012-03-20
> **CProgramming said:**
> 
..........
that's problem start appear yesterday. All worked well before. 

how can I make these HDDs writable again?
..........

Use **gparted** to run a "Check" on each unmounted partition or do a **fsck** on them manually.

---

