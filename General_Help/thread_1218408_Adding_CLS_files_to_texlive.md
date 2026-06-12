---
title: "Adding CLS files to texlive"
date: 2009-07-20
forum: General Help
---

### Post by TomR55 on 2009-07-20
I use (depend) on LateX; that's one of the reasons that I prefer(ed) Linux to Windoze ... seemed that I'd be able to use LaTeX with fewer problems.

Maybe. Maybe not.

I am running (32 bit)Jaunty on an Ibex box.

I've been using LyX, without any problems, for some time now. Now, LyX is fine for most things, but when you have required packages, i.e., class files that you must use to satisfy a publisher, LyX is problematic. 

So, I thought that I'd use texmaker. Obtained this through the package manager. All went well. Tested it on files that I exported from LyX, no problems.

I obtained the CLS files, etc., and installed them in a new directory in 

/usr/share/texmf-texlive/tex/latex 

(Somewhat of a pain to do this because you have to sudo everything, but ok.) 

Next, I ran texhash, also ran mktexlsr for good measure.

But, no matter what I do, texmaker complains (or LaTex complains) that it cannot find the CLS file(s)!

As a reality check, I downloaded a package from CTAN and followed the same installation procedures that I outlined above. Okay, texmaker finds that CLS file.

Perhaps I am missing something simple here? I'm thinking that the next thing will be to install Emacs and write a makefile (yuck!).

Any ideas?

TomR

---

