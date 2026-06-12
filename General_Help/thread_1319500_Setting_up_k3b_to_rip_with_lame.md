---
title: "Setting up k3b to rip with lame"
date: 2009-11-08
forum: General Help
---

### Post by itlarson on 2009-11-08
Can anyone help me set up k3b to rip using lame?  Here is my current command line for lame:

lame --preset extreme --id3v2-only --tt "%t" --ta "%a" --tl "%m" --ty "%y" --tc "%c"  -   "%f"
 

this gives a "command failed" message.  it works on the command line if I insert the wave name in place of the dash.  I have also tried inserting --little-endian which also fails.  What does the "swap byte order" check box do?

Are there any plans to add grip to the repositories? This is what I have used for years, but it isn't available for 9.10.

---

### Post by itlarson on 2009-11-08
Ok, I got it to work with
lame --preset extreme --tn %n --tt %t --ta %a --tl %m --ty %y --tc %c - %f

---

