---
title: "Bin files"
date: 2010-12-18
forum: General Help
---

### Post by el_diablo on 2010-12-18
[SIZE=3]Hi.....
Can anyone plz tell how to look bin files[/SIZE]

---

### Post by karthick87 on 2010-12-18
What you mean by looking bin files??

---

### Post by hakermania on 2010-12-18
"How to look bin files"
nano does open them, but where it cannot read it places @@@

Although you can see all the simple plain text of the executable. DO NOT MODIFY IT! If you modify the simple text you'll probably NOT be able to run the executable again!

---

### Post by surfer on 2010-12-18
binary files are meant to run, not edited.

you can have a look at all the strings in a binary with
```
$ strings executablename
```
but that's about it. what are you trying to achieve?

in order to find out what the binary does you would have to disassemble and anaylze it. veryvery painful! even if you are an expert in that. if you are not: don't do it!

---

