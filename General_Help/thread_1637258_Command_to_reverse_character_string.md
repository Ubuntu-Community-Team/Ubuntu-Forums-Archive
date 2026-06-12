---
title: "Command to reverse character string?"
date: 2010-12-04
forum: General Help
---

### Post by t0p on 2010-12-04
Is there a simple command to reverse a character string?  Eg it takes the string "abcdef12345" and outputs "54321fedcba".

Cheers.

---

### Post by AlphaLexman on 2010-12-04
> **t0p said:**
> Is there a simple command to reverse  the string "abcdef12345" and outputs "54321fedcba".
```
echo "abcdef12345" | rev
```

---

### Post by t0p on 2010-12-04
Thanks AlphaLexman.  That hit the spot quite wonderfully.

---

### Post by sanderj on 2010-12-04
A related nice tool: tac. The reverse of 'cat'. So print *files* in reverse order.

---

### Post by AlphaLexman on 2010-12-04
@ sanderj:

the relevant difference between tac and rev:

'tac' will 'print' to standard output the reverse order of the 'lines' of a file.

'rev' will 'print' to standard output the reverse order of the 'characters' of a file (or standard input.)

---

### Post by sanderj on 2010-12-05
> **AlphaLexman said:**
> @ sanderj:

the relevant difference between tac and rev:

'tac' will 'print' to standard output the reverse order of the 'lines' of a file.

'rev' will 'print' to standard output the reverse order of the 'characters' of a file (or standard input.)

I know. That's why I said "A related nice tool": not the same, but related.

---

