---
title: "Just wondering about..."
date: 2012-03-05
forum: General Help
---

### Post by DoctorVell on 2012-03-05
I don't really know if this belongs in this section, so if it does not I do apologize ahead of time.

I am currently running Windows / Ubuntu 11.10 as a dual boot (with WUBI).  I have a corrupted Windows portion on my main hard drive.  Is it possible for me to copy the folder Ubuntu (where my "disk" is stored) to another hard drive, format the main drive, re-install WUBI and then copy my "disk" of Ubuntu over the one it creates and make it so I don't lose any data/files I installed with Ubuntu?

Thank-you very much I would appreciate any help here or where ever this message does belong (if not here).

Thank-you

---

### Post by DoctorVell on 2012-03-05
ADDITIONAL: If I do copy the "disk" to another disk and copy it back, do I copy the .folders or does it just do the folders too?  If not, is there a way to do that too.

---

### Post by DoctorVell on 2012-03-05
Ignore my own reply, I figured out the answer for that one, but not for the main question.

---

### Post by seawolf167 on 2012-03-05
It would be (IMO) easiest and best to simply move the Wubi install to its own partition. I feel like Wubi is the "trial" version to see if you like it, and if you do and plan to continue using it you should use the "real" version. You can do so following the instructions in [this post]("http://ubuntuforums.org/showthread.php?t=1519354"). 

I don't know too much about the Wubi install particulars, so if you want to do as you originally posted and most it back you'll have to either wait for someone more knowledgeable or see if you can't find anything elsewhere on it.

Here is the [WubiGuide]("https://wiki.ubuntu.com/WubiGuide").

---

### Post by HavarN on 2012-03-05
Wubi uses so called virtual partition(s), a file containing a file system, located on a real parition, inside the "windows" file system. If you backup that file and replace it after you have reinstalled Ubuntu using Wubi, it should be restored.

---

### Post by DoctorVell on 2012-03-05
Thank-you!

---

