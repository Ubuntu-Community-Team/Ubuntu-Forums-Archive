---
title: "I accidentally ran rm -rf on my NTFS partition, is it possible to recover it?"
date: 2011-09-30
forum: General Help
---

### Post by accidentally_rm-rf on 2011-09-30
I have 0 experience in Linux. Decided to give it a try.

I had 3 partitions, 1 for windows, 1 for storage, and 1 for (the newly installed) ubuntu

My friend jokingly told me to enter rm -rf in the terminal and I took him seriously. At the time I had my NTFS storage partition mounted and now it has been erased.

I haven't touched that partition at all because I don't want anything to be overwritten.

I tried to run Recuva and TestDisk but for some reason instead of recovering the files on the drive, it found all the files I had legitimately deleted in the past.

Is there any way I can get my files back?


(i didnt have a backup, but I will from now on :()

---

### Post by nothingspecial on 2011-09-30
Did your "friend" tell you any other commands?

He could be messing with you, I hope.

---

### Post by accidentally_rm-rf on 2011-09-30
> **nothingspecial said:**
> Did your "friend" tell you any other commands?

He could be messing with you, I hope.

nope, just that one command

he was just messing with me, unfortunately i couldnt tell (this was over the internet), and i ran it

i closed the terminal when i noticed something was wrong but by then my linux partition was destroyed (i have since reinstalled), and my NTFS storage partition was empty

---

### Post by nothingspecial on 2011-09-30
If it's a ntfs partition maybe you ought to try some windows recovery software.

There are some good ones that are free to try, as in the will look for your files, then if they do find them you pay for the version that will recover them.

Make sure to bill your "friend".

---

### Post by prodigy_ on 2011-09-30
Any NTFS recovery software should work. I don't think ntfs-3g driver does anything special when it marks files as deleted.

Look here for example:
[http://www.diskinternals.com/](http://www.diskinternals.com/)
[http://www.active-undelete.com/](http://www.active-undelete.com/)

---

### Post by accidentally_rm-rf on 2011-09-30
> **prodigy_ said:**
> Any NTFS recovery software should work. I don't think ntfs-3g driver does anything special when it marks files as deleted.

Look here for example:
[http://www.diskinternals.com/](http://www.diskinternals.com/)
[http://www.active-undelete.com/](http://www.active-undelete.com/)

thanks, ill give those a try


the weird thing is that with the recovery softwares that i've tried so far, they've all just recovered stuff that i actually deleted in the past.

 ive been having a hard time finding the files that were erased by the rm command.

---

### Post by oldos2er on 2011-09-30
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

