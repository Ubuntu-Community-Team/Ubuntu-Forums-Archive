---
title: "Will removing commented lines improve speed?"
date: 2009-08-05
forum: General Help
---

### Post by Intrepid Ibex on 2009-08-05
Just curious as I don't see how could it make any difference.

---

### Post by michy99 on 2009-08-05
Unless you have like a million commented lines in a file, then difference should be so small as to be unnoticeable by a normal human.

---

### Post by PurposeOfReason on 2009-08-05
Speed for what? Commented lines are ignored in every way possible except showing up in a text editor.

---

### Post by mcduck on 2009-08-05
Well, in theory it does. It's just a very, very small difference. :D

I wouldn't care about that, you'd never be able to tell the difference.

---

### Post by Baneblade on 2009-08-05
As previous posters have all said.. yes it does make a difference, but it is so tiny (even with hundreds of comment lines) that you will not be able to see the difference. Dont worry about it, and leave them there.. you never know when you may need to come back and find out what a line does.

On a related note, always make sure you comment your code properly :)

Thread solved?

---

### Post by The Cog on 2009-08-05
An alternative answer would be: No - it may speed up the compilation slightly, but won't affect the compiled object code execution speed.

---

### Post by mcduck on 2009-08-05
> **The Cog said:**
> An alternative answer would be: No - it may speed up the compilation slightly, but won't affect the compiled object code execution speed.

well, that of course applies to compiling code. But the OP didn't mention anything about compiling programs but instead talked about comments in text files in general, so I'd assume he means configuration files and such, not the effect of comments in source code.. ;)

---

### Post by michy99 on 2009-08-05
> **The Cog said:**
> An alternative answer would be: No - it may speed up the compilation slightly, but won't affect the compiled object code execution speed.

Of course that only applies to programs that are compiled.

---

