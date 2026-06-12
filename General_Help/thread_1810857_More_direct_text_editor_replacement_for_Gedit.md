---
title: "More direct text editor replacement for Gedit"
date: 2011-07-23
forum: General Help
---

### Post by nosehat on 2011-07-23
I use a text editor mostly for opening up and editing ascii text files that are used by the programs I write.  For example, manually editing comma separated value data files.

I've been using Gedit for this, and it's been very frustrating because I started noticing new-line characters (hex 0A) were creeping into my CSV ascii data.  It turns out that Gedit has an undocumented "feature" where it silently introduces a new line character at the end of any file you edit, and there is no way to turn this feature off!  ](*,)  See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/379367").  I installed GVim, and a quick test shows that GVim does the same thing.

**I would like a recommendation for a *more straightforward* text editor**, which:

**1) Doesn't add extra bytes to the file** (or if it does, this behavior can be turned off).
**2) Allows you to force ASCII when opening a file** (sometimes Gedit will make an incorrect assumption about encoding because of a stray non-printable character)

More advanced features would be nice, like regular expressions for search and replace, but I need this basic functionality first.

Any recommendations?

Thanks in advance!

---

### Post by JC Cheloven on 2011-07-23
Trying is cheap... I'd expect leafpad to fulfil your needs. It's a simpler nice editor.

---

### Post by hhh on 2011-07-23
> **nosehat said:**
> More advanced features would be nice, like regular expressions for search and replace, but I need this basic functionality first.

Any recommendations?
emacs...
[http://www.gnu.org/software/emacs/tour/](http://www.gnu.org/software/emacs/tour/)

---

### Post by nosehat on 2011-07-27
emacs is definitely the solution here.  Thanks! :)

---

