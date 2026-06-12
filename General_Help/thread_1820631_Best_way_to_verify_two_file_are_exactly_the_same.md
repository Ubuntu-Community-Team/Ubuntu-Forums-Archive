---
title: "Best way to verify two file are exactly the same?"
date: 2011-08-07
forum: General Help
---

### Post by Mouse750 on 2011-08-07
I have a large file that I copied. (very large)

What is the best way to verify the copy is an exact match?

md5sum or is there better?

---

### Post by haqking on 2011-08-07
> **Mouse750 said:**
> I have a large file that I copied. (very large)

What is the best way to verify the copy is an exact match?

md5sum or is there better?

diff <filename1> <filename2>

---

