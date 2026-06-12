---
title: "alias outside terminal? (run dialog etc)"
date: 2012-05-11
forum: General Help
---

### Post by ohnonot on 2012-05-11
just wondering, is it possible to have aliases - or another equally simple and convenient way - working outside the terminal, mostly when using the run dialog?

---

### Post by billyseth on 2012-05-11
an idea is to add your command to a bash script, then put it into your /usr/bin and then it will run from the run dialog, is that something you're looking for?

---

### Post by Oscailt on 2012-05-11
As billyseth has said you can create a bash script and then place it in in either /usr/bin or /usr/sbin

---

### Post by ohnonot on 2012-05-12
yes, thanks, that's exactly what i'm looking for - though the stress was on "as simple and convenient as alias" - on the other hand i could just start using guake again... 
:guitar:

---

### Post by Gyokuro on 2012-05-12
or make a bin dir in $HOME which should be used for such kind of tasks.

---

### Post by ohnonot on 2012-05-12
> **Gyokuro said:**
> or make a bin dir in $HOME which should be used for such kind of tasks.- now *that* works (nota bene: it's ~/bin - no dot)!
run dialog tab completion, perfect.
i might even write a script that does the same as alias - or maybe someone has written it already?
i know, i'm lazy. much nicer to chat on the forum then actually start coding.

---

