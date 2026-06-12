---
title: "update-manager segmentation fault"
date: 2010-10-25
forum: General Help
---

### Post by a__l__a__n on 2010-10-25
My update-manager in ubuntu 10.10 is seg faulting this morning:

[INDENT]alan@linux-1000:~$ sudo update-manager
Segmentation fault[/INDENT]

The UI flashes open for a fraction of a second before it crashes.

I also tried apt-get:
[INDENT]alan@linux-1000:~$ sudo apt-get install -f
Reading package lists... Done
Segmentation faulty tree... 50%
[/INDENT]

Ideas? 
Thanks in advance...

---

### Post by lavinog on 2010-10-25
What happens when you update the package list:
```

sudo apt-get update

```

---

### Post by a__l__a__n on 2010-10-25
That apparently solves the problem.  How simple!

Thanks!!!

---

### Post by stebrepar on 2011-01-16
I just started getting this same problem today with Lucid, but "sudo apt-get update" did not fix it for me. Any more thoughts?
-- 
Stephen

---

### Post by stebrepar on 2011-01-17
Well, it was still broken for me when I booted up this morning. But just now I had it check for updates again, and it seems to have cleared itself up. Strange and a bit worrisome, but at least it seems okay again (for now?).
-- 
Stephen

---

