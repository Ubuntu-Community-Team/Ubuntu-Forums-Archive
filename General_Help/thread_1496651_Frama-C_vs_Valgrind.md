---
title: "Frama-C vs Valgrind"
date: 2010-05-29
forum: General Help
---

### Post by 2uRcJQ34G1 on 2010-05-29
Hiya,

Could someone please enlighten me on the differences between Valgrind and Frama-C. I need tools for debugging my C projects, which are getting too big and complicated to debug. Thanks in advance.

Cheers.

---

### Post by pascal_cuoq on 2010-05-29
**In principle**, the differences between Frama-C and Valgrind are as follows:

**Frama-C** uses static analysis: it tries to produce results that are true for all executions (with some limitations) and interesting, by looking at the source code. It prefers to err on the side of being uninteresting rather than on the side of saying things that are not true for all executions. That is, it may produce false positives, and may produce a lot of them when the analyzed program is just a bit complicated. On the other hand, if you understand the limitations and get Frama-C to tell you that there will never be (say) an invalid pointer access in the program, it means that there will really never be an invalid pointer access in any of the executions, even if there are billions of possible inputs and as many different executions.

**Valgrind** uses dynamic analysis: the results it offers are for one execution at a time. Valgrind may miss a problem (such as an invalid pointer access) by accident some of the times: that's a false negative. But usually, when it warns about a problem, the problem is real (it does not have "false positives" in general, although you may disagree with its definition of what a "problem" is).

**In practice**:

If your program is already big and you didn't write it with the intent of verifying it formally from the beginning, you'll probably get more interesting results from Valgrind than from Frama-C. But do not let this warning prevent you from taking a look at what the latter can do on smaller programs without dynamic allocation if you are curious.

---

### Post by 2uRcJQ34G1 on 2010-05-30
Thanks a lot mate, that did clear up a lot of my questions. Upon reading your analysis, I think I might as well install both of them, since I tend to modularise large programs and if I have both I might catch an error that might be overlooked by one of the program that might be caught by the other one.

I welcome new perspectives as well.

Cheers.

---

### Post by dino99 on 2010-05-30
valgrind is the tool mainly used by ubuntu devs

---

### Post by 2uRcJQ34G1 on 2010-06-03
I just installed Frama-C, it downloaded a whole lot of other junk(i dont need them) softwares. And after trying it out, I figured it is NOT what I need. I am now using Valgrind, it seems more useful.

Cheers to all who replied.

---

