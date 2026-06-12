---
title: "Acidrip and /dev/null"
date: 2006-06-02
forum: General Help
---

### Post by feight on 2006-06-02
Okay, I've always been told that /dev/null was basicly a black hole; something that software dumped data to be destroyed. Why does acidrip send data there on the first pass of a two pass XVID encoding?

Thank you ahead of time.

---

### Post by deeek on 2006-06-02
If I am not mistaken, the reason why it sends the "output" of the first pass to /dev/null is that for 2 pass encoding you only need the divx2pass.log file for the second pass, so why waste space.

---

### Post by feight on 2006-06-02
Ahhh! I had not known there was a log file created. I'll have to make sure I delete the previous one first then. I'm floundering a bit since Acidrip is broken in it's current incarnation, at least in Dapper. 
 You have to take the information from the debug log and put it in the command prompt and remove an extra colon to make the script run so I've been trying to learn more about Mencoder which is what Acidrip is a script for.

 Thank you very much for enlightening me.

---

