---
title: "Difficulty installing Java software (involves CLASSPATH)"
date: 2010-09-02
forum: General Help
---

### Post by Scarlette on 2010-09-02
Hi all,

I'm having a bit of trouble installing some software I plan to use for an upcoming project. It's a natural language processing tool, known as a "shallow parser" (also called a "chunker" by some NLP researchers). 

This is the software I'm trying to install: [http://cogcomp.cs.illinois.edu/page/software_view/13](http://cogcomp.cs.illinois.edu/page/software_view/13)

It requires that I first install the Learning Based Java (LBJ2) language [[http://cogcomp.cs.illinois.edu/page/software_view/11]](http://cogcomp.cs.illinois.edu/page/software_view/11]), which I seem to have done successfully using Jakarta Ant (but I'm not 100% certain I was successful). It also requires that I install the Part of Speech tagger (POS) [[http://cogcomp.cs.illinois.edu/page/software_view/3]](http://cogcomp.cs.illinois.edu/page/software_view/3]) which seems to be the point at which I'm failing. When I try to install this, I'm told:

```
Exception in thread "main" java.lang.NoClassDefFoundError: LBJ2/Main
```I thought I'd set up the CLASSPATH correctly, but something isn't right.

Is there any good Samaritan out there who could install these three things and walk me through the process they went through?

If it helps, I'm using Ubuntu pretty much right out of the box.

Best,
S

---

