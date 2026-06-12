---
title: "sudo: no tty present and no askpass program specified"
date: 2012-02-26
forum: General Help
---

### Post by ashish061291 on 2012-02-26
Hi...

I am trying to the open source tool "fio" through my code.
But for that i have to run it as root and when i run it it gives me the following error.

"sudo: no tty present and no askpass program specified"

what to do ??

Thnx
Ashish

---

### Post by oldos2er on 2012-02-26
Moved to General Help.

---

### Post by Khayyam on 2012-02-26
> **ashish061291 said:**
> I am trying to the open source tool "fio" through my code. But for that i have to run it as root and when i run it it gives me the following error: "sudo: no tty present and no askpass program specified"

My psychic powers of reading your "code" via the aether are obviously failing. So, how are you "running it"? How are you providing a password to sudo? What "code"?

```
% sudo mycode
```

or

```
#!/bin/bash

sudo mycode
```

Are you using sudo's '-A' switch? .. I could try to guess, but without more information that's all it'd be.

best ... khay

---

