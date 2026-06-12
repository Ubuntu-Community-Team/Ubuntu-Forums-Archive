---
title: "Copying files in Ubuntu - Benefit in using LiveCD?"
date: 2010-01-07
forum: General Help
---

### Post by Pipps on 2010-01-07
If I wished to copy 400GB of files from one independent drive to an entirely separate physical drive, would it be best to do so within LiveCD, rather than within a Ubuntu installation which is located on a separate partition but within the same physical drive on which the files are to be copied from?

Would LiveCD provide any copying performance benefits in such a situation?

---

### Post by MelDJ on 2010-01-07
i think doing it with the live cd will be slower.

---

### Post by audiomick on 2010-01-07
I don't know of any reason to do it from the live CD, and as melDJ said, it might be slower.

---

### Post by Pipps on 2010-01-07
I should be grateful to understand your reasoning.

Why exactly would LiveCD be slower? :)

---

### Post by slakkie on 2010-01-07
livecd is always slower, coz it runs only in RAM.

However, when copying your homedir for example it is safer not to use any of the files when copying since it might get corrupted, in that case a copy when running from a livecd would be safer (in theory).

You could also have a look at rsync to copy files.

---

### Post by Pipps on 2010-01-07
Does Rsync copy files faster than Nautilus?

---

### Post by slakkie on 2010-01-07
> **Pipps said:**
> Does Rsync copy files faster than Nautilus?

No, bit slower, but it deals better with resources so you can continue to work without a laggy system.

---

### Post by Pipps on 2010-01-07
That is very useful to know!

Thank you, Sir! :)

---

