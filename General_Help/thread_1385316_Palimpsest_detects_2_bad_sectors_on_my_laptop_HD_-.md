---
title: "Palimpsest detects 2 bad sectors on my laptop HD - is this a problem?"
date: 2010-01-19
forum: General Help
---

### Post by Mike_IronFist on 2010-01-19
I opened the Palimpsest disk utility to check my newly-purchased 500 GB (internal) laptop hard drive. It said that my disk has 2 bad sectors, but the overall assessment was that my hard drive is fine. Now, my old internal hard drive had 28 bad sectors. I didn't notice any issues with either hard drive, but I recently read about the horrors caused by bad sectors and I'm wondering if having just 2 bad sectors is an issue. Palimpsest says that the 2 bad sectors will be remapped if the disk attempts to write to them and fails doing so. What does this mean for me?

(Just a note, if possible I'd like an answer from someone who genuinely knows the subject, rather than someone who just attempted to Google search it. No offense, but I looked on Google for an answer myself and found nothing that was conclusive in helping me figure this out.)

---

### Post by JiuJitsu500 on 2010-01-19
There are two kinds of bad sectors I know of. As long as you haven't noticed any problems with either hard drives, no, not to worry (usually a sign of age and being re-written a hundred times). As long as GParted can format (or whichever program you like) the disk you're fine for a few years.... even longer if you don't delete and re-write much.

Anywho though, "software type" bad sectors are simply mistakes made form errors in writing, happens to everything often enough to be annoying, but no real threat until they get too bad. Luckily, these are correctable with an advanced software tool to do so. But unfortunately, sometimes it requires complete wiping and re-formatting of the disk.

"Hardware type" bad sectors though are not possible to correct unless you have the ability to take the discs out and fix the mechanical error. These disks as I'm sure you know spin between roughly 5400-7200rpm, so as you can imagine it's fairly easy to knock the computer and cause an error that scratches or otherwise ruins part of the disk. Hopefully, small nudges or just enough to move those lasers and crazines inside just cause soft sectors....

Like I said though, it shouldn't be too much to worry about, my year old 500GB is now reporting 200 or so bad sectors after I accidentally erased it (the Ubuntu disk utility lead me worng... read my HD and my flash drive backwards) and it still works fine.

---

### Post by Mike_IronFist on 2010-01-19
> **JiuJitsu500 said:**
> There are two kinds of bad sectors I know of. As long as you haven't noticed any problems with either hard drives, no, not to worry (usually a sign of age and being re-written a hundred times). As long as GParted can format (or whichever program you like) the disk you're fine for a few years.... even longer if you don't delete and re-write much.

Anywho though, "software type" bad sectors are simply mistakes made form errors in writing, happens to everything often enough to be annoying, but no real threat until they get too bad. Luckily, these are correctable with an advanced software tool to do so. But unfortunately, sometimes it requires complete wiping and re-formatting of the disk.

"Hardware type" bad sectors though are not possible to correct unless you have the ability to take the discs out and fix the mechanical error. These disks as I'm sure you know spin between roughly 5400-7200rpm, so as you can imagine it's fairly easy to knock the computer and cause an error that scratches or otherwise ruins part of the disk. Hopefully, small nudges or just enough to move those lasers and crazines inside just cause soft sectors....

Like I said though, it shouldn't be too much to worry about, my year old 500GB is now reporting 200 or so bad sectors after I accidentally erased it (the Ubuntu disk utility lead me worng... read my HD and my flash drive backwards) and it still works fine.
Thank you very much for your response, this is exactly the information I needed to know. I'm glad to know that my hard drive will be okay.

---

