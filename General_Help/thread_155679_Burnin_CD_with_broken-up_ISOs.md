---
title: "Burnin CD with broken-up ISOs"
date: 2006-04-05
forum: General Help
---

### Post by izzydahedgehog on 2006-04-05
I downloaded a CD where the ISO file is broken up into about 25 different pieces and then compressed as .rar files.  The readme page that came with it says to use Nero or Alcohol 120%, but those are Windows apps.

Is there any way that K3b will do this job?  Is there a way that I can get ArK to somehow extract all these different pieces into one file?

Thanks in advance.

---

### Post by localzuk on 2006-04-05
You should be able to use ark on the first .rar file (split files are usually .r01 .r02 etc...). You may need to install unrar, which is available by installing the extra repositories ([https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)) and installing the unrar package.

---

### Post by izzydahedgehog on 2006-04-06
Woops!  You're right; I tried unraring the first one about an hour after I posted that and it worked.  Thanks.

PS: What's the deal with the "unrar-free" package?  Free software is great, but it didn't seem to work that well.  Or, at all.

---

