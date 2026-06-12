---
title: "Encrypted Swap Partition?"
date: 2010-07-01
forum: General Help
---

### Post by riph72 on 2010-07-01
Hello all,

I read an article earlier that suggested the swap partition is encrypted by default if you select an encrypted /home folder during installation, is that true (for Lucid)?

I am suspecting it isn't because my hibernation works, which I believe shouldn't be the case?

Cheers,
Richard.

---

### Post by nutznboltz on 2010-07-01
Hmm, just because regular swap is encrypted does not imply that hibernation is also encrypted.  Hibernation uses swap space in a way that demand paging does not.

---

### Post by riph72 on 2010-07-01
So you're saying (if I understand you correctly) that regular swap is encrypted, but hibernation swap isn't?

So as long as I avoid using hibernation, there is no danger of unencrypted data lurking in swap during "normal" use?

---

### Post by nutznboltz on 2010-07-01
I'm saying that just because hibernation works you cannot jump to the conclusion that your swap spaces are not encrypted.

---

