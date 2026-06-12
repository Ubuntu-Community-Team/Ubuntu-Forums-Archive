---
title: "Help installing G77 compiler"
date: 2009-09-05
forum: General Help
---

### Post by SrEstroncio on 2009-09-05
Hello everyone, I was wondering if someone could help me install the g77 compiler for the Fortran 77 programming language, according to google it is included in the GCC package, but according to the gcc manual gcc is a C and C++ compiler.

kinda lost here, any help would be appreciated

---

### Post by starcraft.man on 2009-09-05
> **SrEstroncio said:**
> Hello everyone, I was wondering if someone could help me install the g77 compiler for the Fortran 77 programming language, according to google it is included in the GCC package, but according to the gcc manual gcc is a C and C++ compiler.

kinda lost here, any help would be appreciated

The answer appears to be gfortran. [G77 appears to be deprecated.]("http://en.wikipedia.org/wiki/Gfortran")

I'd install the build-essential package as well as gfortran from the repos. I know nothing about fortran itself, I assume you can handle that. Though I'm a bit confused now, just read it's included in gcc past 4.1, yet gfortran is still separate package. I think you'll need to reasearch a bit, but with both packages ya should have all ya need to go.

---

### Post by Stan_1936 on 2009-11-13
Can anyone answer the original question?  I'm trying to do the same thing but am confused about the process.

Is there how-to?

Please help.

---

### Post by krishnamohan on 2009-12-05
You can install gcc and g77 is included...gcc 3.4 should do it..the latest versions don't have g77...

Search in
***[http://packages.ubuntu.com/](http://packages.ubuntu.com/)***

if you are not able to get it by synaptic....

---

### Post by Miguel on 2009-12-05
I would basically forget about g77 and go directly to gfortran. Although it is mainly a F90 compiler, you should have no issues compiling FORTRAN 77 code with it. I know, I've done it. 

In some instances, you may be hit by some "deprecated" features, that aren't part of the standard FORTRAN 77. This happens, for example, if you try to compile David Vanderbilt's USPP package. This is managed with the flag "-std=legacy".

In short,
```

sudo aptitude install build-essential gfortran

```
and set F77=gfortran -std=legacy.

---

