---
title: "overwriting"
date: 2010-05-06
forum: General Help
---

### Post by myke50 on 2010-05-06
hello people, need some help. how do i overwrite a file.?

---

### Post by luigi_mb on 2010-05-06
> **myke50 said:**
> hello people, need some help. how do i overwrite a file.?

To overwrite, say, file-a, with, say, file-b, just

```

cp file-a file-b

```

Suggestion: first make a copy of file-b, to avoid later ... oops!

/luigi

---

### Post by jbrown96 on 2010-05-06
You mean like a secure erase? There's nothing fool-proof, but shred is a good way. You can read about the possible insecurities with ```
man shred
``` overwrite ```
sudo shred -vvn 5 FILE
``` that will overwrite it five times with random data. For small files, it should be instant, for larger things it can take some time, but that will give you plently of status messages.

---

