---
title: "BASH not recognizing characters"
date: 2009-08-04
forum: General Help
---

### Post by ooolongT on 2009-08-04
I am trying to use awk to help me with a parsing issue I have.  What I need to do is to move some columns around that have somewhat odd field separators. The easiest way for me to describe the problem is to give you a screen shot of the issue (see attachment).

As you can see the box in the middle of p[]p is not coming up. It comes up in Kate, which is set to ISO-8859-1, but so is BASH.  Why does this character not come up in BASH?  More importantly, why does it not process the box character?  What can I do about it?

---

### Post by kjohri on 2009-08-05
Try to use the escape sequence for that character. Or, you can first find out the exact hexcode of the character in the input file using hexdump command and then proceed.

---

