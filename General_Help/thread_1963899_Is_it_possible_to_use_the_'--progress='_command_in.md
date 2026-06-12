---
title: "Is it possible to use the '--progress=' command in any set script or terminal command"
date: 2012-04-23
forum: General Help
---

### Post by AlexOnVinyl on 2012-04-23
I was reading man pages on the **wget** command and saw that if I wanted a standard ascii bar i just had to specify ```
--progress=
``` then either put ```
dot
``` or ```
bar
``` can this be used elsewhere in other scripts for programs?

---

### Post by r-senior on 2012-04-23
Only if it's written into the program itself, it's not a standard thing across the board.

---

### Post by AlexOnVinyl on 2012-04-23
> **r-senior said:**
> Only if it's written into the program itself, it's not a standard thing across the board.

Thank you. is there anyway I could find out?

---

### Post by Vaphell on 2012-04-23
most commands support -h/--help switch that prints their available options. My experience tells me that most don't provide anything like that

---

### Post by Cheesemill on 2012-04-23
Read the man page for the program your interested in?

---

### Post by AlexOnVinyl on 2012-04-23
> **Vaphell said:**
> most commands support -h/--help switch that prints their available options. My experience tells me that most don't provide anything like that

That's sad, I love the little ASCII bar.. :(

> **Cheesemill said:**
> Read the man page for the program your interested in?

Yeah I usually do, but sometimes the Man pages don't give a very good example of the use of a certain situation.

---

