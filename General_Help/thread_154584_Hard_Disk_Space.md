---
title: "Hard Disk Space"
date: 2006-04-03
forum: General Help
---

### Post by snowjunkie on 2006-04-03
Hi everyone,

I have a 9gb partition on my laptop, I have Kubuntu 6.06 installed on it.  I've been using Ubuntu since hoary and have basically being dist-upgrading since.  The disk has only 2gb free out the 9gb.  

I think that's a lot, but I have no idea on the usual points to look for junk files that can be deleted.  

My home folder takes up 1.6gb, so the rest of the files (5.4gb) are apps and ubuntu base files... is that about average for most people?

Thanks!

---

### Post by jimbren on 2006-04-03
I know it doesn't really answer your question, but I recently started using durep to generate some easily read reports on disk space usage.  It is pretty handy, and makes it a lot easier to find the bloat.

---

### Post by Ptero-4 on 2006-04-03
The first point where the junk hides is in /var/cache/apt/archive . There's where apt dumps all the debs it downloads when you install stuff through adept/synaptic.

---

### Post by aysiu on 2006-04-03
That's not average, but it's conceivable--depending on how many apps you have. Minus my data files (which I keep on a separate partition), my Ubuntu is pretty close to 3 GB, and I have a fairly light installation (few applications installed).

---

