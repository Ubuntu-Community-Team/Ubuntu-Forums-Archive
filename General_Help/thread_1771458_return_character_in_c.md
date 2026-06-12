---
title: "return character in c?"
date: 2011-05-30
forum: General Help
---

### Post by javajames97 on 2011-05-30
i am writing in C (with C++) and i want to be able to test if someone has just pressed the enter key without entering anything. i am using getch which is unbuffered and so should accept enter key character. But for the life of me i can't remember what charater (or indeed character combination) would represent the newline/return key. Could somebody please help me?

---

### Post by javajames97 on 2011-05-30
wait, no it's just \n:
if (char=='\n') { works fine }

---

