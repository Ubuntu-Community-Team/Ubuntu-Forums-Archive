---
title: "LaTeX to pdf error"
date: 2009-07-16
forum: General Help
---

### Post by sripplinger on 2009-07-16
I'm writing my thesis using Lyx as a LaTeX front end.  When I try to create a pdf I get the following error:

```
LaTeX Error: Option clash for package geometry.

```
It also gives me the following details:

```
 \geometry
              {verbose,tmargin=2.5cm,bmargin=2.5cm,rmargin=2.5cm}
The package geometry has already been loaded with options:
  []
There has now been an attempt to load it with options
  [letterpaper]
Adding the global options:
  ,letterpaper
to your \documentclass declaration may fix this.
Try typing  <return>  to proceed.
```

The line they are referring to is in the thesis document class file provided by my university.  Any thoughts on why I might be getting this error and what I can do to fix it?

---

### Post by XCan on 2009-07-16
It sounds like you've specified the papersize in two places. Without more of your preamble, it's hard to know for sure.

---

### Post by sripplinger on 2009-07-16
I figured the same thing, but I'm not sure where I need to fix it.  I've attached the LaTeX class file (the Lyx layout is in the tar file, too, though I don't think it is part of the problem).  Do you think I should just delete the lines in the class file which specify the paper size?

---

### Post by XCan on 2009-07-16
Hmm, well the .cls file is unreadable. However, I was referring to what your first line in your main file contains, i.e., \documentclass[options]{some_template}

---

### Post by sripplinger on 2009-07-16
Sorry about that file.  I got a corrupt one mixed in there somehow.

Anyway, I think I've got it figured out now.  The .cls file has a few lines specifying page margins.  Apparently the version of Lyx that I am running either doesn't see this or doesn't care and just goes right ahead with its own geometry specifications.  That's where the redundancy was coming from.  I commented out that section of my .cls file, did a texhash and all was well.

Thanks for your help.

---

